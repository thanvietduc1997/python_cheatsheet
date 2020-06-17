# My personal python cheatsheet

## OpenCV image <-> base64

### OpenCV image -> base64

```Python
import cv2
import base64

img = cv2.imread('demo.jpg') # img is np.ndarray
# retval is True, buffer is np.ndarray of bytes
retval, buffer = cv2.imencode('.jpg', img)
# img_base64 is base64 string
img_base64 = base64.b64encode(buffer)
```

### Base64 -> OpenCV image

```Python
import cv2
import base64

# img_bin is type of bytes
img_bin = base64.b64decode(img_base64)
# we need to convert it to np.ndarray first
# but first we need to convert bytes to bytearray
img_bin_np = bytearray(img_bin)
img_bin_np = np.asarray(img_bin_np)
# retrieve the image
img = cv2.imdecode(img_bin_np, flags=cv2.IMREAD_COLOR)
```
