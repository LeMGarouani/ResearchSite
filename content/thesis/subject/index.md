+++
title = "Noise detection in stereoscopic synthesis images using machine learning"
date = "2018-10-02"


# Publication type.
# Legend:
# 0 = Uncategorized
# 1 = Conference proceedings
# 2 = Journal
# 3 = Work in progress
# 4 = Technical report
# 5 = Book
# 6 = Book chapter
# 7 = Thesis
publication_types = ["7"]

# Publication name and optional abbreviated version.
publication = ""
publication_short = ""

# Abstract and optional shortened version.
abstract = "Modeling a generic noise detection model in stereoscopic images (consideration of different media) in order to reduce the computation time for generating one or more synthesized images"

abstract_short = ""

# Featured image thumbnail (optional)
image_preview = ""

# Is this a selected publication? (true/false)
selected = false

# Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter the filename (excluding '.md') of your project file in `content/project/`.
projects = []

# Links (optional).
url_pdf = ""
url_preprint = ""
url_code = ""
url_dataset = ""
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = "http://www-lisic.univ-littoral.fr/spip.php?article351"

# Does the content use math formatting?
math = true

# Does the content use source code highlighting?
highlight = true

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
[header]
image = ""
caption = ""

+++

**Team:** Imap <br> **Supervisors:** C. Renaud, S. Delepoulle

Lighting simulation methods, used in image synthesis, make it possible to obtain so-called photo-realistic views of virtual environments. To do this, they use stochastic methods, which explore the space of the light paths and are characterized by a progressive convergence of the image towards the solution. This progressiveness is visually reflected by the presence of noise, which must be identified and quantified in order to have perceptual criteria for stopping algorithms in each area of the image. This is all the more important since the calculation times of an image are counted in hours, even in ten hours of calculation. Having reliable criteria for stopping calculations at different points in an image would therefore allow significant time savings.

The approaches we are studying to do this within the IMAP team, are based on supervised and semi-supervised learning techniques, which have provided interesting results in the framework of classical images, in two dimensions. The objective of this thesis is to study the extension of these techniques to the case of images perceived in relief, for which several images must be calculated (two for a classical stereoscopic vision, a larger number for auto-stereoscopic devices), with for corollary a consequent increase of the required calculation times. A first difficulty of the project lies in the multiplicity of peripherals and technologies available for the restitution of the relief effect, which must lead to a fine analysis of the noise perception thresholds on each of them. This task will be carried out in collaboration with psychologists from the University of Lille, specialized in perception. A second phase of the work will consist in searching for the learning tools best able to provide a correct answer to the problem of noise perception in images.

This thesis is part of the ANR PrISE-3D project, which aims at a better understanding of the perceptual mechanisms underlying the perception of a quality image, in front of various stereoscopic restitution peripherals. The results obtained should make it possible (i) to reduce the computing time required to produce high quality images and (ii) to consider the development of interactive rendering algorithms that can be used in large immersive environments.

**Keywords:** lighting simulation, visual perception, automatic learning, classification

**Goal:** Modeling a generic noise detection model in stereoscopic images (consideration of different media) in order to reduce the computation time for generating one or more synthesized images
