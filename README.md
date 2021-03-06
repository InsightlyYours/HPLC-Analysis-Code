# HPLC-Analysis-Code
This is a set of MATLAB m-files that allows the interactive analysis and editing of HPLC data.

They were written over the cours of a number of years (approximately 2006 to 2012) and are presented as is.  They were used to analyze exported Shimadzu HPLC data, including that from an RID Detector, a UV Detector, and later a MALLS detector.  When used in conjunction with the appropriate calibrations, they could be used to quantify the number of molecules of specific molecular weights, look at branched copolymers, and other polymeric system.  Those calibrations are, in some m-files, hard coded in.  In others, they were input as user inputs.  Everyone is free to use them as the license dictates, but considering the specificity of the application and the wide variety of available software and analysis packages, they may not be relevant to your systems.  They are, in general, not sufficiently explained in comments and I will not be updating the comments.  I have uploaded them for nostalgic and demonstration reasons.

The m-files are both production and deprecated versions, uploaded without differentiation.  Some were used as standalone files, some were used in larger MATLAB command line programs, and some are interchangeable.  Some were also used in the modeling of polymer chains, which is stored more explicitly in a separate repository on my account.  It is possible that those (or these) have inter-dependencies that prevent functioning without the other files.  There may also be redundancies and copies in both repositories, though I attempted to minimize that.  This also contains script files that are merely long lists of commands to analyze data.  That data is not here, but the scripts can provide some information on how to properly call the m-files as well as the bulk analysis capabilities.

GetGPCData.m was used to extract, transform, and load data into MATLAB.

TransformX.m uses HPLC calibration curves to convert the x-ais from elution time to PS molecular weight.  It gives the user the option of choosing the calibration curve appropriate to when the data was taken.

TransformPStoOther.m converts a PS molecular weight axis to the molecular weight axis of any other polymer used based upon the Mark-Hourwink-Sakurada coefficients.

BaselineChoice.m allows the subtraction of baseline drift or noise from the data.  Options are a linear drift or a curve that is fit to the tail of the solvent peak (based upon an average of 10 independently run solvent peaks).

FitLine.m is a function used by BaselineChoice.m that fits a line to the baseline.

SubtractTail.m is a function used by BaselineChoice.m that fits the solvent tail.

TheFit.m contains the coefficients and assignments for SubtractTail.m.

Histogram.m linearized the distribution of the chain.  It takes the molecular weight axis in number of monomers which, due to the nonlinearity of separation, are often fractional according to the calibration curve and converts the x-axis into degree of polymerization, N.  It also bins the data such that it is also only for whole numbers of monomers.  It does this by averaging the fractional polymer lenghts and placing the results in the nearest whole number.

AreaNormalize.m uses the trapezoidal Reiman sum to calculate the area under a user-specified curve.

HeightNorm.m takes user-specified data and normalizes its maximum height in a specified range to the same range in a control.  It was extended to also subtract off the control peak after normalization, determine the percent depletion, scale the subtracted peak by that, and calculate the area of the residual change in distribution.  All the advanced options are included in varargin.

MolWDist.m calculates the number average, weight average, and PDI of the input distribution.

SameX.m shifts the distrbution on the x-axis to match the ocation of a user-specified peak.  Used in adjustment to internal standards.
