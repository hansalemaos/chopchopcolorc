# Locate RGB colors faster than ever with this efficient color search module (C + multiprocessing)!

## pip install chopchopcolorc


## Tested against Python 3.11 / Windows 10


### In Action - one CPU only:

[![YT](https://i.ytimg.com/vi/bhLRYlK0cts/maxresdefault.jpg)](https://www.youtube.com/watch?v=bhLRYlK0cts)
[https://www.youtube.com/watch?v=bhLRYlK0cts]()


```python
This module provides functions for parallel color search in a collection of images.
It utilizes multiprocessing and a code written in C to efficiently process images concurrently.

Functions:
1. **_color_search_c(pic, colors):**
    - Internal function for color search in a single image.
    - Utilizes the 'locate_pixelcolor_c' module to search for specified colors.
    - Returns an array of coordinates where the colors are found.

2. **color_search_c(pics, rgb_tuples, cpus=5, chunks=1, print_stderr=True, print_stdout=False, usecache=True):**
    - Executes parallel color search on a list of images using multiprocessing.
    - Utilizes '_color_search_c' for each image in parallel.
    - Returns a dictionary with image indices mapped to their corresponding color search results.

Example Usage:
    from chopchopcolorc import color_search_c
    from list_all_files_recursively import get_folder_file_complete_path # optional
    folder=r"C:\testfolderall"
    colors2find = (
        (69, 71, 66),
        (255, 255, 255),
        (153, 155, 144),
        (55, 57, 52),
        (136, 138, 127),
        (56, 58, 53),
        (54, 56, 51),
        (0, 180, 252),
    )
    allpi = [
        x.path
        for x in get_folder_file_complete_path(folder)
        if x.ext == ".png"
    ]


    colorresults=color_search_c(pics=allpi, rgb_tuples=colors2find, cpus=6, chunks=1, print_stderr=True,
    print_stdout=False, usecache=True,)
    print(colorresults)


```