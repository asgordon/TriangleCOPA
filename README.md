TriangleCOPA
============
TriangleCOPA is a set of 100 animations, questions, and texts based on the original Heider-Simmel film, involving the interactions between a big triangle, a small triangle, a circle in and around a box with a door. It serves as a development dataset and integrated evaluation of automated perception, interpretation, and narration. 

## 1. Interpretation Questions

The term COPA is an acronym for "Choice of Plausible Alternatives," referring to a style of question for use in evaluating commonsense reasoning systems. Each question consists of a given premise and question, and two plausible alternatives - one of which is consistently selected by people. 

TriangleCOPA consists of 100 COPA questions in the domain of the Heider-Simmel film. Each question was validated by multiple human raters.

In addition, TriangleCOPA includes logical formalizations of each question and alternative, encoded in first-order predicate calculus using a controlled vocabulary. 

Details about these 100 questions and their logical encodings can be found in the following paper:

* Maslan, N., Roemmele, M., and Gordon, A. (2015) One Hundred Challenge Problems for Logical Formalizations of Commonsense Psychology. Twelfth International Symposium on Logical Formalizations of Commonsense Reasoning (Commonsense-2015), March 23-25, 2015, Stanford, CA.

## 2. Animations

Included are 100 short movies in the style of the original Heider-Simmel film, involving the interactions between a big triangle, a small triangle, a circle in and around a box with a door. Each animation was created by Nicole Maslan using the "Heider-Simmel Interactive Theater" application, described in the following paper:

* Gordon, A. and Roemmele, M. (2014) An Authoring Tool for Movies in the Style of Heider and Simmel. In A. Mitchell et al. (Eds.): International Conference on Interactive Digital Storytelling, Singapore, November 3-6, 2014 (ICIDS-2014), LNCS 8832, pp. 49--60. Springer International Publishing Switzerland (2014).
 
Each line of TriCOPA-animations.csv contains the data for an animation that depicts the premise of a TriCOPA question. Each line is a CSV (comma-separated) row with the following columns:

Performance_ID (a unique ID for each animation, different from the COPA question number)

Performance_Label_ID (the item number of the COPA question, consistent with TriCOPA.txt; also has a brief title describing the premise)

Shape1_Name Shape2_Name Shape3_Name Shape4_Name	(a list of the shapes that appear in the animation)

The rest of the columns contain the position and rotation data for each shape in the animation. Each shape has a series of x-coordinate, y-coordinate, and rotation (in radians) values, one value for each frame of the animation. The frame data is linearly interpolated so that a new frame occurs at every 20ms of the animation (the first value in the list is at time 0). The shape indices correspond to their order in the previous column (i.e. the values for Shape1_Name are X1_Values, Y1_Values, R1_Values, the values for Shape2_Name are X2_Values, Y2_Values, R2_Values, etc.).

An SVG file (TriCOPA-stage.svg) is included as a reference for character and stage geometry.

## 3. Narrations

Included are 100 short textual narratives of each movie that align with the correct interpretation in each TriCOPA question, written by Nicole Maslan.


## 4. Charades-datasets

If it were possible to automatically recognize humanlike actions in the animation data, then one could develop a system that answered TriangleCOPA questions given only the object trajectories as input. The following papers describe a supervised machine learning approach to this problem.

* Roemmele, M., Morgens, S., Gordon, A., and Morency, L. (2016) Recognizing Human Actions in the Motion Trajectories of Shapes. Proceedings of ACM Intelligent User Interfaces, March 7-10, 2016, Sonoma, CA.
* Roemmele, M., Archer-McClellan, H., and Gordon, A. (2014) Triangle Charades: A Data-Collection Game for Recognizing Actions in Motion Trajectories. 2014 International Conference on Intelligent User Interfaces, February 24-27, 2014, Haifa, Israel.

Included here are the training and test datasets collected as part of this research.

In each dataset folder (OneCharacterData and TwoCharacterData) are the training and testing files for that dataset (performances.train and performances.test). Each file is in CSV format, with one animation per line. For each animation, the following columns are given:

* Performance ID: unique numerical ID for each animation
* Performance Label ID: action label for that animation (appears as string)
* Shape Names: index numbers associated with each shape (For 1-character data, there is only one shape, so X1, Y1, R1 always refer to bigTriangle; for 2-character data, shape1 with trajectory data X1, Y1, R1 is bigTriangle and shape2 with X2, Y2, R2 is littleTriangle.)
* X1_Values: the series of x-coordinate positions of shape 1 across the animation (20 ms between each value) (repeated for shape 2)
* Y1_Values: the series of y-coordinate positions of shape 1 across the animation (20 ms between each value) (repeated for shape 2)
* R1_Values: the series of shape 1's orientations (in radians) across the animation (20 ms between each value) (repeated for shape 2)

