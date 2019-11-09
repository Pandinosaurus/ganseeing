Seeing What a GAN Cannot Generate
=================================

State-of-the art GANs can create increasingly realistic images, yet
they are not perfect.

What is a GAN *unable* to generate?
This repository contains the code for the ICCV 2019 paper
[Seeing What a GAN Cannot Generate](
http://ganseeing.csail.mit.edu/papers/seeing.pdf), which introduces
a framework that can be used to answer this question.

![](img/906_r.png) | ![](img/906_t_anon.png)
:-----------------:|:-----------------------:
GAN reconstruction |       Real photo 

Our goal is *not* to benchmark *how far* the generated
distribution is from the target.  Instead, we want to
visualize and understand *what* is different between real
and fake images.

## Mode-dropping and the problem of visualizing omissions

We visualize the omissions of an image generator in two ways.

   1. We identify omissions within the *distribution* of images.
   2. We identify omissions within *individual* images.

## Seeing omissions in the distribution

To understand omissions in a GAN's output distribution, we compare
segmentation statistics between the GAN output and the training
distribution.

A Progressive GAN trained to generate LSUN outdoor church images
is analyzed below.

![](img/progan-church-histogram.png)

The model does not generate enough pixels of people, cars, fences,
palm trees, or signboards compared to the training distribution.
The script `run_fsd.sh` and the notebook `seeing_distributions.ipynb`
show how we collect and visualize these segmentation statistics.

## Seeing omissions in individual images

To understand omission in specific GAN-generated output, we must pair
the output with a real photo that shows what the GAN *should* have
drawn but did not.  So we compare real training photos to a
reconstructed image derived from the model of the GAN.

These visualizations are created by `run_invert.sh`.

### People

As seen in the distribution statistics, thie GAN does not draw enough
people.  By visualizing reconstructions, we can see how: the GAN seems
to avoid drawing large person figures entirely, instead synthesizing
plausible scenes without people.

GAN reconstruction              | Real photo 
:------------------------------:|:------------------------------:
![](img/church_393_reconst.png) | ![](img/church_393_target.png)
![](img/church_523_reconst.png) | ![](img/church_523_target.png)
![](img/church_646_reconst.png) | ![](img/church_646_target.png)
![](img/church_569_reconst.png) | ![](img/church_569_target.png)

<!---
![](img/church_120_reconst.png) | ![](img/church_120_target.png)
![](img/church_200_reconst.png) | ![](img/church_200_target.png)
![](img/church_401_reconst.png) | ![](img/church_401_target.png)
![](img/church_447_reconst.png) | ![](img/church_447_target.png)
![](img/church_457_reconst.png) | ![](img/church_457_target.png)
![](img/church_463_reconst.png) | ![](img/church_463_target.png)
![](img/church_594_reconst.png) | ![](img/church_594_target.png)
--->

### Vehicles

A similar effect is seen for vehicles.

GAN reconstruction              | Real photo 
:------------------------------:|:------------------------------:
![](img/church_54_reconst.png)  | ![](img/church_54_target.png)
![](img/church_666_reconst.png) | ![](img/church_666_target.png)
![](img/church_27_reconst.png)  | ![](img/church_27_target.png)

<!---
![](img/church_522_reconst.png) | ![](img/church_522_target.png)
![](img/church_296_reconst.png) | ![](img/church_296_target.png)
![](img/church_90_reconst.png)  | ![](img/church_90_target.png)
![](img/church_645_reconst.png) | ![](img/church_645_target.png)
--->

### Signs

GAN reconstruction              | Real photo 
:------------------------------:|:------------------------------:
![](img/church_43_reconst.png)  | ![](img/church_43_target.png)
![](img/church_264_reconst.png) | ![](img/church_264_target.png)
![](img/church_72_reconst.png)  | ![](img/church_72_target.png)

### Monuments

GAN reconstruction              | Real photo 
:------------------------------:|:------------------------------:
![](img/church_41_reconst.png)  | ![](img/church_41_target.png)
![](img/church_480_reconst.png) | ![](img/church_480_target.png)
![](img/church_271_reconst.png) | ![](img/church_271_target.png)
<!---
![](img/church_303_reconst.png) | ![](img/church_303_target.png)
--->

### Palm trees

GAN reconstruction              | Real photo 
:------------------------------:|:------------------------------:
![](img/church_568_reconst.png) | ![](img/church_568_target.png)

