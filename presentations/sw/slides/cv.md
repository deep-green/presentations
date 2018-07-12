class: center, middle
# CV / Bilderkennung

---

## Technologie
### CV/Bilderkennung

__Programmiersprache(n):__
- Python

__Bibliotheken:__
- OpenCV
- NumPy

---

## Methoden und Algorithmen
### CV/Bilderkennung

- Bildnormierung: OpenCV.resize, OpenCV.cvtColor
- Noise-Reduction: OpenCV.GaussianBlur, OpenCV.bilateralFilter
- Kontrasterhöhung: OpenCV.createCLAHE, OpenCV.threshold
- Kantenerkennung: OpenCV.Canny
- Linienerkennung: OpenCV.HoughLinesP
- Lageberechnung: OpenCV.initCameraMatrix2D, OpenCV.solvePnP
- Projektion: OpenCV.Rodrigues, OpenCV.projectPoints
- Templateerkennung: OpenCV.matchTemplate, OpenCV.minMaxLoc

---

## Workflow
### CV/Bilderkennung

- Erkennen der Lage des Schachbretts
- Berechnung der Projektion und der Kameradaten
- Erkennen der Grenzen des Schachbretts
- Erkennen der Belegung des Schachbretts
- Erkennen der Figuren

---

## Workflow - Lage des Schachbretts
### CV/Bilderkennung

<center><img src="images/cv_middle_lines.png" width="75%" /></center>

---

## Lage des Schachbretts - Code-Snippets
### CV/Bilderkennung

```python
# toolchain to get best verticals
def toolchain_02(given_image, already_used_angle):
    image_original = given_image
    image_resize = resize(image_original)
    image_blur = blur(image_resize);
    image_gray = gray(image_blur);
    image_clahe = clahe(image_gray);
    image_canny = canny(image_clahe);
    line_set = houghlinesp(image_canny);
    line_list = chess_math.get_list_from_linearray(line_set)
    # divide the houghlines in two parts
    line_list_vertical = chess_math.divide_line_list_by_direction(line_list, 1)
    average_angle = chess_math.get_average_angle(line_list_vertical)
    if abs(average_angle-already_used_angle) < 45/180 * math.pi:
        line_list_vertical = chess_math.divide_line_list_by_direction(line_list, 0)
    line_list_vertical = chess_math.expand_lines_to_image_size(line_list_vertical, image_resize.shape[1], image_resize.shape[0])
    line_list_vertical = chess_math.homogen_lines(line_list_vertical)
    line_list_vertical = chess_math.delete_identical_lines_from_list(line_list_vertical)
    if debug > 1:
        image_result = draw_line_list(image_resize, line_list_vertical, (255, 0, 0), 1)
        cv2.imshow("Debug Window", image_result)
        cv2.waitKey(debug_delay_time)
    return line_list_vertical
```

---

## Workflow - Berechnung der Projektion
### CV/Bilderkennung

<center><img src="images/cv_projection.png" width="80%" /></center>

---

## Projektion - Code-Snippets
### CV/Bilderkennung

```python

    # define world coordinates of the chess field
    chess_field_size = 50.0
    world_point_1 = [0.0, 0.0, 0.0]
    world_point_2 = [chess_field_size, 0.0, 0.0]
    world_point_3 = [0.0, chess_field_size, 0.0]
    world_point_4 = [chess_field_size, chess_field_size, 0.0]
    world_points = [world_point_1, world_point_2, world_point_3, world_point_4]

    # get initial camera matrix
    initial_camera_matrix = chess_math.get_camera_matrix(camera_points, chess_field_size, image_width, image_height)

```

---

## Projektion - Code-Snippets
### CV/Bilderkennung

```python

    # calculate rotation vector and translation vector via solvePnP
    dist_coeffs = np.zeros((4, 1))  # Assuming no lens distortion
    model_points = np.array(world_points,np.float32)
    image_points = np.array(camera_points, np.float32)
    (success, rotation_vector, translation_vector) = cv2.solvePnP(model_points, image_points, initial_camera_matrix, dist_coeffs, flags=cv2.SOLVEPNP_ITERATIVE)


```

---

## Projektion - Verfeinerung
### CV/Bilderkennung

<center><img src="images/cv_raster.png" width="75%" /></center>

---

## Workflow - Ermittlung der Kameradaten
### CV/Bilderkennung

<center><img src="images/cv_swing.png" width="100%" /></center>


---

## Kameradaten - Code-Snippets
### CV/Bilderkennung

```python

    # calculate rotation matrix out of the rotation vector via Rodrigues
    rmat = cv2.Rodrigues(rotation_vector)[0]

    # calculate the Euler angles from the rotation matrix
    beta = -math.acos(rmat[2, 2])
    alpha = math.acos(rmat[2, 1] / math.sin(beta))
    if (abs(math.sin(alpha) * math.sin(beta) - rmat[2, 0]) > 0.0001):
        alpha = alpha
    gamma = math.asin(rmat[0, 2] / math.sin(beta))
    if (abs(-1 * math.sin(beta) * math.cos(gamma) - rmat[1, 2]) > 0.0001):
        gamma = math.pi - gamma
    rotation_matrix = chess_math.rotation_matrix_from_euler_angles(alpha, beta, gamma)

```

<center><img src="images/cv_debug_camera.png" width="30%" /></center>

---

## Workflow - Grenzen des Schachbretts
### CV/Bilderkennung

<center><img src="images/cv_threshold.png" width="75%" /></center>

---

## Workflow - Grenzen des Schachbretts
### CV/Bilderkennung

```python

field colors detected:
----------------------

   ['0', [1], [2], [3], [4], [5], [6], [7], [8], [9], [10, [11, [12, [13, [14, [15
100[' ', ' ', 'w', ' ', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', ' ', 'w']
101[' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']
102[' ', ' ', 'u', ' ', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', ' ', 'b']
103[' ', ' ', 'u', ' ', 'u', 'u', 'b', 'u', 'b', 'u', 'b', 'u', 'b', 'u', ' ', 'b']
104[' ', ' ', 'u', ' ', 'u', 'b', 'u', 'b', 'u', 'b', 'u', 'b', 'u', 'u', ' ', 'u']
105[' ', ' ', 'b', ' ', 'u', 'u', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'u', ' ', 'b']
106[' ', ' ', 'b', ' ', 'u', 'b', 'u', 'b', 'w', 'b', 'w', 'b', 'u', 'u', ' ', 'u']
107[' ', ' ', ' ', ' ', 'u', 'u', 'b', 'u', 'b', 'u', 'b', 'u', 'b', 'u', ' ', 'b']
108[' ', ' ', ' ', ' ', 'u', 'u', 'u', 'b', 'u', 'u', 'u', 'u', 'u', 'u', ' ', 'b']
109[' ', ' ', ' ', ' ', 'u', 'w', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', ' ', 'u']
110[' ', ' ', ' ', ' ', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', ' ', ' ']
111[' ', ' ', ' ', ' ', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', ' ', ' ']
112[' ', ' ', ' ', ' ', ' ', 'b', 'b', 'b', 'u', 'u', 'b', 'b', 'b', ' ', ' ', ' ']
113[' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']
114[' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']
115[' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']

```

---


## Workflow - Grenzen des Schachbretts
### CV/Bilderkennung

```python

best matching color scheme and board direction:
-----------------------------------------------
best_start_column : 5
best_start_line   : 3
target_line       : ['w', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'w', 'w', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'w', 'w', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'w', 'w', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'w']
best_line         : ['u', 'b', 'u', 'b', 'u', 'b', 'u', 'b', 'b', 'u', 'b', 'u', 'b', 'u', 'b', 'u', 'u', 'b', 'w', 'b', 'w', 'b', 'w', 'b', 'b', 'u', 'b', 'w', 'b', 'w', 'b', 'u', 'u', 'b', 'u', 'b', 'u', 'b', 'u', 'b', 'u', 'u', 'b', 'u', 'u', 'u', 'u', 'u', 'w', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u', 'u']
board direction   : right
max_ranking       : 27
max_ranking_wrong : 27
max_ranking_right : 27

```


---

## Workflow - Grenzen des Schachbretts
### CV/Bilderkennung

<center><img src="images/cv_corners.png" width="75%" /></center>

---
