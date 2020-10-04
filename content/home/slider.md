+++
# Slider widget.
widget = "slider"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = false  # Activate this widget? true/false
weight = 25  # Order that this section will appear.

# Slide interval.
# Use `false` to disable animation or enter a time in ms, e.g. `5000` (5s).
interval = 5000

# Slide height (optional).
# E.g. `500px` for 500 pixels or `calc(100vh - 70px)` for full screen.
height = "calc(100vh - 70px)"

# Slides.
# Duplicate an `[[item]]` block to add more slides.
[[item]]
  title = ""
  content = "<div style=\"display: block; height: 100vh; width: 400vw; margin: auto;\"></div>"
#  content = "<div style=\"height: 50vh;width: 60pxi\"></div>"
  #"![Cloud Practitioner](https://images.youracclaim.com/size/680x680/images/1fdcf6a9-de8e-4e35-96b0-e801d8411506/AWS-CloudPractitioner.png){ width=20% }"
  align = "left"  # Choose `center`, `left`, or `right`.
  # Overlay a color or image (optional).
  #   Deactivate an option by commenting out the line, prefixing it with `#`.
  overlay_color = "#666"  # An HTML color value.
  overlay_img = "aws.jpg"  # Image path relative to your `static/media/` folder.
  overlay_filter = 0.5  # Darken the image. Value in range 0-1.

[[item]]
  title = ""
  content = ""
  align = "left"

  overlay_color = "#555"  # An HTML color value.
  overlay_img = "gcp.png"  # Image path relative to your `static/media/` folder.
  overlay_filter = 0.5  # Darken the image. Value in range 0-1.

[[item]]
  title = ""
  content = ""
  align = "right"

  overlay_color = "#333"  # An HTML color value.
  overlay_img = "rosh.jpg"  # Image path relative to your `static/media/` folder.
  overlay_filter = 0.5  # Darken the image. Value in range 0-1.
+++
