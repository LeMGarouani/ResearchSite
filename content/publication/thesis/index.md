+++
title = "Machine learning methods for noise detection in computer generated images"
date = "2022-01-08"

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Jérôme Buisine"]

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
publication_types = ["7"]
publication_typename = "Thesis"

# Publication name and optional abbreviated version.
publication = ""
publication_short = ""

# Summary. An optional shortened abstract.
summary = "Lighting simulation methods, used in image synthesis, make it possible to obtain so-called photorealistic views of 3D virtual environments. To do this, they use stochastic methods, based on the theory of large numbers, which explore the space of light paths and are characterised by a progressive convergence of the image towards the solution. This progressiveness is visually expressed by the presence of noise, which is gradually reduced as the calculations progress. This noise must be identified and quantified in order to have perceptual criteria for stopping the algorithms in the different areas of the image. This is all the more important as the calculation time for an image can be counted in hours or even tens of hours. Having reliable criteria to stop the calculations at different points of an image would therefore allow significant time savings. In this thesis, we propose to use statistical and machine learning methods for the reduction and detection of this generated noise. The contributions made in the framework of this thesis are: (i) the constitution of a base of synthetic images with the collection of human subjective thresholds of the residual noise, (ii) the study and management of a highly perceptible local noise, (iii) the creation of deep learning models on this base of labelled images and (iv) a phase of validation of the reconstructed images obtained (learned or not) from the models of perception from subjective evaluations. Related work to the thesis research area, notably concerning the management of a specific noise in images called firefly, has been proposed, as well as the application of a method allowing the targeting of the noise characteristics studied. "

# Digital Object Identifier (DOI)
doi = ""

# Is this a featured publication? (true/false)
featured = false

# Tags (optional).
#   Set `tags = []` for no tags, or use the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["Lighting simulation", "Machine Learning", "Noise detection", "Deep learning"]

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
url_pdf = "https://hal.archives-ouvertes.fr/tel-03527737"
url_code = ""
url_dataset = ""
url_project = ""
url_slides = "sources/thesis/soutenance/main.pdf"
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