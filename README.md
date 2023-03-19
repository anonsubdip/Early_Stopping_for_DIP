# Test Early Stopping for Deep Image Prior with architectural changes and for CT reconstruction

This is a fork of the official implementation of the paper [*Early Stopping for Deep Image Prior*](https://arxiv.org/pdf/2112.06074.pdf).


While experimenting with the [Subspace-DIP](https://github.com/anonsubdip/subspace_dip) for CT reconstruction, we had difficulties to use the variance-based early stopping criterion proposed in above work. In order to identify changes that could potentially hinder this criterion to be effective in our scenarios.

Differences between our scenarios in [Subspace-DIP](https://github.com/anonsubdip/subspace_dip) and the setup in [*Early Stopping for Deep Image Prior*](https://arxiv.org/pdf/2112.06074.pdf) include:

* Our network uses GroupNorm instead of BatchNorm
* Our network does *not* include a sigmoid activation on the output
* We consider CT reconstruction problems, so our forward operator is a ray transform instead of the identity operator

The plots below show results when changing a single or multiple of these aspects.

# Denoising (identity operator)

## Original [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV.ipynb">ES_WMV.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/225988132-0d3ae5eb-7930-4bec-9235-efe94fce452a.png" alt="my alt text"/>
</figure>

## Without sigmoid output [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-no_sigmoid.ipynb">ES_WMV-no_sigmoid.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/225988666-6dbb9307-fb1e-4d58-ab93-c18bf18cb0ab.png" alt="my alt text"/>
</figure>

## Using GroupNorm [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-GN.ipynb">ES_WMV-GN.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/225988961-40229642-0beb-4cce-b177-6c48b9700ab4.png" alt="my alt text"/>
</figure>

# Low-dose CT reconstruction (ray transform with many angles and high noise)

## Original [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-CT-low_dose.ipynb">ES_WMV-CT-low_dose.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/225989724-1ab895f4-aa99-490b-92fa-a2a3d25a0d14.png" alt="my alt text"/>
</figure>

## Without sigmoid output [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-CT-low_dose-no_sigmoid.ipynb">ES_WMV-CT-low_dose-no_sigmoid.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/225989742-341dd752-d2f8-467e-bfe2-d615137db8fb.png" alt="my alt text"/>
</figure>

## Using GroupNorm [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-CT-low_dose-GN.ipynb">ES_WMV-CT-low_dose-GN.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/226168947-3626683f-27f8-42b2-8669-586eee1d90aa.png" alt="my alt text"/>
</figure>

## Without sigmoid output, using GroupNorm [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-CT-low_dose-no_sigmoid-GN.ipynb">ES_WMV-CT-low_dose-no_sigmoid-GN.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/226112063-05a0d750-7b92-4638-8041-ee1b159e1a15.png" alt="my alt text"/>
</figure>

# Sparse-view CT reconstruction (ray transform with few angles and moderate noise)

## Original [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-CT-sparse_view.ipynb">ES_WMV-CT-sparse_view.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/225990332-78db9893-cf39-4211-9c7e-09791d3bc611.png" alt="my alt text"/>
</figure>

## Without sigmoid output [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-CT-sparse_view-no_sigmoid.ipynb">ES_WMV-CT-sparse_view-no_sigmoid.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/225990344-668f6acf-1c64-44d0-84d1-c92ac6c6967c.png" alt="my alt text"/>
</figure>

## Using GroupNorm [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-CT-sparse_view-GN.ipynb">ES_WMV-CT-sparse_view-GN.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/226168980-8e4ca027-4c0a-4219-b73c-71c20882f48b.png" alt="my alt text"/>
</figure>

## Without sigmoid output, using GroupNorm [<a href="https://github.com/anonsubdip/Early_Stopping_for_DIP/blob/main/ES_WMV-CT-sparse_view-no_sigmoid-GN.ipynb">ES_WMV-CT-sparse_view-no_sigmoid-GN.ipynb</a>]
<figure>
  <img src="https://user-images.githubusercontent.com/123627605/226112089-18fdc325-a58e-4674-8a26-d08dc4f847f2.png" alt="my alt text"/>
</figure>
