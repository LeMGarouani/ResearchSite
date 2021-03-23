+++
title = "Subjective human thresholds over computer generated images"
date = "2021-02-22"

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Jérôme Buisine" , "Samuel Delepoulle", "Rémi Synave", "Christophe Renaud"]

# Publication type.
# Legend:
# 0 = Uncategorized
# 1 = Conference paper
# 2 = Journal article
# 3 = Preprint / Working Paper
# 4 = Report
# 5 = Book
# 6 = Book section
# 7 = Thesis
# 8 = Patent
publication_types = ["0"]
publication_typename = "Dataset"

# Publication name and optional abbreviated version.
publication = "Zenodo"
publication_short = ""

# Summary. An optional shortened abstract.
summary = "This proposed dataset is composed of 80 points of view of photo realistics images with different level of samples (following the Monte Carlo approach) for each. Each image is 800 x 800 pixels in size. The most noisy image is of 20 samples and the reference one (the most converged image obtained) is of 10000 samples. The pbrt rendering engine (version 3) was used to generate these images."

# Digital Object Identifier (DOI)
doi = "10.5281/zenodo.4531460"

# Is this a featured publication? (true/false)
featured = false

# Tags (optional).
#   Set `tags = []` for no tags, or use the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["Source Themes"]

# Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["deep-learning"]` references 
#   `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects = []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references 
#   `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides = ""

# Links (optional).
url_pdf = ""
url_code = ""
url_dataset = "https://zenodo.org/record/4531460"
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = ""

# Custom links (optional).
#   Uncomment line below to enable. For multiple links, use the form `[{...}, {...}, {...}]`.
# links = [{name = "Custom Link", url = "http://example.org"}]

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
[image]
  # Caption (optional)
  caption = "Image credit: [**Unsplash**](https://unsplash.com/photos/s9CC2SKySJM)"

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = ""


#{{% alert note %}}
#Supplementary notes can be added here, including [code and math](https://sourcethemes.com/academic/docs/writing-markdown-latex/).
#{{% /alert %}}
+++

Realistic image computation mimics the natural process of acquiring pictures by simulating the physical interactions of light between all the objects, lights and cameras lying within a modelled 3D scene. This process is known as global illumination and was formalised by Kajiya with the following rendering Equation:

$L_o(x, \omega_o) = {L_e(x, \omega_o)} + \int_{\Omega}^{} {L_i(x, \omega_i)} \cdot f_r(x, \omega_i \rightarrow \omega_o) \cdot \cos \theta_i d\omega_i$

where:

  - $L_o(x, \omega_o)$ is the luminance traveling from point $x$ in direction $\omega_o$;
  - $L_e(x, \omega_o)$ is point $x$ emitted luminance (it is null if point x does not lie on a ligth source surface);
  the integral represents the set of luminances $L_i$ incident in $x$ from the hemisphere of the directions $\Omega$ and reflected in the direction $\omega_o$. The reflected luminances are weighted by the materials reflecting properties (bidirectionnal reflectance function $f_r(x, \omega_i \rightarrow \omega_o)$) and the cosinus of the incident angle.


This equation cannot be analytically solved and Monte Carlo approaches are generally used to estimate the value of the pixels of the final image.

This proposed dataset is composed of 80 points of view of photo realistics images with different level of samples (following the Monte Carlo approach) for each. Each image is 800 x 800 pixels in size. The most noisy image is of 20 samples and the reference one (the most converged image obtained) is of 10000 samples. The pbrt rendering engine (version 3) was used to generate these images.

By exploiting these levels of samples obtained and therefore of noise perceptible in the images, average subjective human thresholds were collected. For this purpose, the images were divided into 16 areas of 200 x 200 pixels in size for each point of view.

The proposed image database is composed of the following files:

  - **human-thresholds.csv**: the set of human subjective thresholds obtained on 40 points of view. A line is composed of the name of the point of view followed by all the thresholds obtained for each of the 16 zones;
  - **SIN3D_dataset.tar.gz**: is an archive containing all the images from 20 to 10000 samples in steps of 20 samples for each point of view (i.e. 500 images per point of view). Each folder in the archive corresponds to a point of view.

This image database has been exploited in order to propose an objective model for noise detection in photo-realistic computer-generated images (article referenced to this image database).

**Funding:** This research was funded by ANR support: project ANR-17-CE38-0009.