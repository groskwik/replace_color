# Color Replacement Tool

This Python script processes all PNG files in the current directory, replacing a specified target color with a replacement color within a given threshold. It offers an optional feature to check if the target color is present in sufficient quantity before proceeding with the replacement.

## Features

- **Color Replacement**: Replaces a specific color in PNG images with another color, considering a specified threshold for color similarity.
- **Quantity Check**: Optionally checks if the target color is present in a minimum number of pixels before performing the replacement.

## Requirements

- Python 3.x
- `Pillow` library for image processing

## Installation

1. **Install Python**: Ensure you have Python 3 installed. You can download it from the [official Python website](https://www.python.org/).

2. **Install Pillow**: Install the Pillow library using pip:

   ```bash
   pip install pillow
   ```

## Usage

Run the script from the command line with the following options:

```bash
python script_name.py --target-color TARGET_COLOR [--replace-color REPLACE_COLOR] [--threshold THRESHOLD] [--quantity-threshold QUANTITY_THRESHOLD] [--quantity-check]
```

### Arguments

- `--target-color`: **(Required)** Hex code of the color to replace (e.g., `#FF0000`).

- `--replace-color`: Hex code of the replacement color (default: `#FFFFFF`).

- `--threshold`: Threshold for color replacement (0 to 100, default: 0). This defines the maximum allowed color difference for a pixel to be considered a match.

- `--quantity-threshold`: Minimum number of target color pixels required to process a file (default: 1000). Used only if `--quantity-check` is enabled.

- `--quantity-check`: Enable quantity check for the target color before processing. If this flag is set, the script will only process files where the target color is present in at least `quantity_threshold` pixels.

### Example

Replace the color `#FF0000` with `#00FF00` in all PNG files in the current directory, considering a threshold of 10:

```bash
python script_name.py --target-color #FF0000 --replace-color #00FF00 --threshold 10
```

## Functions

- `hex_to_rgb(hex_color)`: Converts a hex color string to an RGB tuple.

- `is_color_close(pixel_color, target_color, threshold)`: Checks if the pixel color is close to the target color within a specified threshold.

- `color_quantity_check(image_path, target_color, threshold, quantity_threshold)`: Checks if the target color is present in a large quantity within a threshold in the given image.

- `replace_color(image_path, target_color, replacement_color, threshold)`: Replaces a specific color in an image with another color within a threshold.

- `process_folder(target_hex_color, replacement_hex_color, threshold, quantity_threshold, check_quantity)`: Processes all PNG files in the current folder, replacing the target color with the replacement color based on the provided parameters.

## Notes

- Ensure that the script has permission to read and write files in the current directory.

- The script saves the modified images with a prefix `p_` added to the original filename.

- The threshold value determines how closely a pixel's color must match the target color to be replaced. A higher threshold allows for more variation in color matching.

## License

This project is licensed under the MIT License. 
