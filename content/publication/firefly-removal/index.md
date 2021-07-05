+++
title = "Firefly Removal in Monte Carlo Rendering with Adaptive Median of meaNs"
date = "2021-06-29"

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Jérôme Buisine" , "Samuel Delepoulle", "Christophe Renaud"]

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
publication_types = ["1"]
publication_typename = "Conference Paper"

# Publication name and optional abbreviated version.
publication = "Eurographics Symposium on Rendering, Saarbrücken, Germany"
publication_short = ""

# Summary. An optional shortened abstract.
summary = "Estimating the rendering equation using Monte Carlo methods produces photorealistic images by evaluating a large number of samples of the rendering equation per pixel. The final value for each pixel is then calculated as the average of the contribution of each sample. The mean is a good estimator, but not necessarily robust which explains the appearance of some visual artifacts such as fireflies, due to an overestimation of the value of the mean. The MoN (Median of meaNs) is a more robust estimator than the mean which allows to reduce the impact of outliers which are the cause of these fireflies. However, this method converges more slowly than the mean, which reduces its interest for pixels whose distribution does not contain outliers. To overcome this problem we propose an extension of the MoN based on the Gini coefficient in order to exploit the best of the two estimators during the computation. This approach is simple to implement whatever the integrator and does not require complex parameterization. Finally, it presents a reduced computational overhead and leads to the disappearance of fireflies."

# Digital Object Identifier (DOI)
doi = "10.2312/sr.20211296"

# Is this a featured publication? (true/false)
featured = false

# Tags (optional).
#   Set `tags = []` for no tags, or use the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["Monte Carlo Techniques", "Global Illumination", "Sampling and Reconstruction"]

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
url_pdf = "https://diglib.eg.org/bitstream/handle/10.2312/sr20211296/121-132.pdf"
url_code = ""
url_dataset = ""
url_project = "https://diglib.eg.org/handle/10.2312/sr20211296"
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

Estimating the rendering equation using Monte Carlo methods produces photorealistic images by evaluating a large number of samples of the rendering equation per pixel. The final value for each pixel is then calculated as the average of the contribution of each sample. The mean is a good estimator, but not necessarily robust which explains the appearance of some visual artifacts such as fireflies, due to an overestimation of the value of the mean. The MoN (Median of meaNs) is a more robust estimator than the mean which allows to reduce the impact of outliers which are the cause of these fireflies. However, this method converges more slowly than the mean, which reduces its interest for pixels whose distribution does not contain outliers. To overcome this problem we propose an extension of the MoN based on the Gini coefficient in order to exploit the best of the two estimators during the computation. This approach is simple to implement whatever the integrator and does not require complex parameterization. Finally, it presents a reduced computational overhead and leads to the disappearance of fireflies.

**Funding:** This research was funded by ANR support: project ANR-17-CE38-0009.