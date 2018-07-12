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
- Erkennen des Musters des Schachbretts
- Erkennen der Grenzen des Schachbretts
- Erkennen der Belegung des Schachbretts
- Erkennen der Figuren

---

## Workflow
### Lage des Schachbretts

<center><img src="images/cv_middle_lines.png" width="95%" /></center>

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

## Workflow
### Berechnung der Projektion

<center><img src="images/cv_projection.png" width="95%" /></center>

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

---

## Workflow
### Kameradaten

<img src="cv_swing.png" width="95%" />

---

## Kameradaten - Code-Snippets
### CV/Bilderkennung

```python

    # calculate rotation vector and translation vector via solvePnP
    dist_coeffs = np.zeros((4, 1))  # Assuming no lens distortion
    model_points = np.array(world_points,np.float32)
    image_points = np.array(camera_points, np.float32)
    (success, rotation_vector, translation_vector) = cv2.solvePnP(model_points, image_points, initial_camera_matrix, dist_coeffs, flags=cv2.SOLVEPNP_ITERATIVE)

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
