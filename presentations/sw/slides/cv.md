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
- Erkennen der Grenzen des Schachbretts



<br>

## Code-Snippets
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
