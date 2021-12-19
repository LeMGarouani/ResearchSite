+++
title = "Guided-Generative Network for noise detection in Monte-Carlo rendering"
date = "2021-12-13"

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Jérôme Buisine" , "Fabien Teytaud", "Samuel Delepoulle", "Christophe Renaud"]

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
publication_typename = "Conference"

# Publication name and optional abbreviated version.
publication = "International Conference On Machine Learning And Applications"
publication_short = "ICMLA 2021"

# Summary. An optional shortened abstract.
summary = "Estimating the features to be extracted from an image for classification tasks are sometimes difficult, especially if images are related to a particular kind of noise. The aim of this paper is to propose a neural network architecture named Guided-Generative Network (GGN) to extract refined information that allows to correctly quantify the noise present in a sliding window of images. GNN tends to find the desired features to address such a problem in order to emit a detection criterion of this noise. The proposed GGN is applied on photorealistic images which are rendered by Monte-Carlo methods by evaluating a large number of samples per pixel. An insufficient number of samples per pixel tends to result in residual noise which is very noticeable to humans. This noise can be reduced by increasing the number of samples, as proven by Monte-Carlo theory, but this involves considerable computational time. Finding the right number of samples needed for human observers to perceive no noise is still an open problem. The results obtained show that GGN can correctly solve the problem without prior knowledge of the noise while being competitive with existing methods."

# Digital Object Identifier (DOI)
doi = ""

# Is this a featured publication? (true/false)
featured = false

# Tags (optional).
#   Set `tags = []` for no tags, or use the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["Deep Learning", "GAN", "Monte-Carlo", "Computer Graphics", "Noise detection"]

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
slides = "sources/thesis/papers/icmla_2021/main.pdf"

# Links (optional).
url_pdf = "https://hal.archives-ouvertes.fr/hal-03374214/"
url_code = "https://github.com/prise-3d/GAN-Percept"
url_dataset = "https://zenodo.org/record/4531460"
url_project = ""
url_slides = "sources/thesis/papers/icmla_2021/main.pdf"
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


The estimation of image quality and noise perception still remains an important issue in various image processing applications. It has also become a hot topic in the field of photo-realistic computer graphics where noise is inherent in the calculation process. Unlike natural-scene images, however, a reference image is not available for computer-generated images. Thus, classic methods to assess noise quantity and stopping criterion during the rendering process are not usable. This is particularly important in the case of global illumination methods based on stochastic techniques: They provide photo-realistic images which are, however, corrupted by stochastic noise. This noise can be reduced by increasing the number of paths, as proved by Monte Carlo theory, but the problem of finding the right number of paths that are required in order to ensure that human observers cannot perceive any noise is still open. Until now, the features taking part in the human evaluation of image quality and the remaining perceived noise are not precisely known. Synthetic image generation tends to be very expensive and the produced datasets are high-dimensional datasets. In that case, finding a stopping criterion using a learning framework is a challenging task. In this paper, a new method for characterizing computational noise for computer generated images is presented. The noise is represented by the entropy of the singular value decomposition of each block composing an image. These Singular Value Decomposition (SVD)-entropy values are then used as input to a recurrent neural network architecture model in order to extract image noise and in predicting a visual convergence threshold of different parts of any image. Thus a new no-reference image quality assessment is proposed using the relation between SVD-Entropy and perceptual quality, based on a sequence of distorted images. Experiments show that the proposed method, compared with experimental psycho-visual scores, demonstrates a good consistency between these scores and stopping criterion measures that we obtain.