---
title: SHReturnTapers (Fortran)
keywords: spherical harmonics software package, spherical harmonic transform, legendre functions, multitaper spectral analysis, fortran, Python, gravity, magnetic field
sidebar: mydoc_sidebar
permalink: shreturntapers.html
summary:
tags: [fortran]
toc: false
editdoc: fdoc
---

Calculate the eigenfunctions of the spherical-cap concentration problem.

## Usage

call SHReturnTapers (`theta0`, `lmax`, `tapers`, `eigenvalues`, `taper_order`, `exitstatus`)

## Parameters

`theta0` : input, real\*8
:   The angular radius of the spherical cap in radians.

`lmax` : input, integer
:   The spherical harmonic bandwidth of the localization windows.

`tapers` : output, real\*8, dimension (`lmax`+1, (`lmax`+1)\*\*2)
:   The spherical harmonic coefficients of the `(lmax+1)**2` localization windows. Each column contains the coefficients of a single window that possesses non-zero coefficients for the single angular order specified in `taper_order`. The first and last rows of each column correspond to spherical harmonic degrees 0 and `lmax`, respectively, and the columns are arranged from best to worst concentrated.

`eigenvalues` : output, real\*8, dimension ((`lmax`+1)\*\*2)
:   The concentration factors of the localization windows.

`taper_order` : output, integer, dimension ((`lmax`+1)\*\*2)
:   The angular order of the non-zero spherical harmonic coefficients in each column of `tapers`.

`exitstatus` : output, optional, integer
:   If present, instead of executing a STOP when an error is encountered, the variable exitstatus will be returned describing the error. 0 = No errors; 1 = Improper dimensions of input array; 2 = Improper bounds for input variable; 3 = Error allocating memory; 4 = File IO error.

## Description

`SHReturnTapers` will calculate the eigenfunctions (i.e., localization windows) of the spherical-cap concentration problem. Each column of the matrix `tapers` contains the spherical harmonic coefficients of a single window and the corresponding concentration factor is given in the array `eigenvalues`. Each window has non-zero coefficients for only a single angular order that is specified in `taper_order`: all other spherical harmonic coefficients for a given window are identically zero. The columns of `tapers` are ordered from best to worst concentrated, and the first and last rows of each column correspond to spherical harmonic degrees 0 and `lmax`, respectively. The localization windows are normalized such that they have unit power.

## References

Wieczorek, M. A. and F. J. Simons, Localized spectral analysis on the sphere, 
Geophys. J. Int., 162, 655-675, 2005.

Simons, F.J., F.A. Dahlen, and M.A. Wieczorek, Spatiospectral concentration on a sphere, SIAM Review, 48, 504-536, 2006.

## See also

[shreturntapersm](shreturntapersm.html), [computedg82](computedg82.html), [computedm](computedm.html)
