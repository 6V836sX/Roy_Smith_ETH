 Okay, let's begin. I think we're recording now. But before I begin today, are there any
 questions from last week? Okay, let me start. Well, this week I was going to focus on convex optimisation. And as you can probably realise, I'm kind of making this up as I go along in terms of what we're covering. But after some discussions, particularly with Jeremy Watson, I thought we'd start with convex optimisation for this
 week. And I would cover the basic convex optimisation today. And then maybe tomorrow I'd move on to linear matrix inequalities, or LMIs. Maybe today, we'll see how far we get. Which are a form of convex optimisation, it's very general, and you can pose a lot of problems in that form.
 You may or may not have seen something like this before. Yes? Sorry? Yeah, it's a specialisation, or you can think of it as a generalisation, but it's sequential quadratic programming, as you're thinking about. So no, it's similar, very, very similar. They are quadratic programs, or more specifically, semi-definite programs.
 And then, maybe on Wednesday, or maybe I'll start it tomorrow, MPC, which stands for Model Predictive Control, which I think you probably have seen a little bit of. And so I'll go into more of that as well, and try and combine these other two things.
 Okay, so that's sort of the plan. And we'll see where we get to. So I wanted to start off by just putting down the basic definitions, which you're probably all familiar with. And to do this a little more formally, I'll start off with the idea of convex sets, and then go to convex functions, and then convex optimisation problems.
 But convex sets are any sort of set. Think of just a region of the plane. And a set is convex if a line segment you draw between any two points in it is also in the set. So, you know, the obvious picture, you have some sort of set like this.
 One point here, one point here, and then you draw a line between them. If it's inside the set, you get a convex set, or it's a convex set. But, you know, obviously sets that look like this are not convex. You can expect points here where this region, of course, goes outside the set.
 So that's a basic definition. You could write it mathematically this way. Gamma times x1, instead. That was x1 and x2. Gamma between 0 and 1 just covers all the points in between, everything on the line. So you could write it like that. So any particular choice you have, this is also in the set.
 All right. I can give you some examples. The first one is another type of set, and that's called a cone. So, a cone, actually, the thing to think of is an ice cream cone, basically. It has a pointed tip in here.
 It's a cone if, for any element in the set, any positive scaling of that element, gamma where gamma goes from 0 to infinity, is also in the set. So, you know, sets like, for example, this, everything in here, that would be a cone.
 Because no matter what you have in here and here, when you take any point, and then every scaling is in it. So it goes all the way up to infinity.
 This is kind of suggestive of a cone we'll talk about a bit more tomorrow. And that's the cone, which is essentially the entire positive orthant.
 It's an important cone. But anyway, that's the definition of a cone. Notice that it doesn't have to be convex. These examples I've drawn here are convex in that, and we will hope to focus on convex sets, but if I just chose, say, two vectors like this, this and this, and this is actually my set, this L-shaped thing going all the way up to infinity, that's a cone.
 Because any element in the set, pick that element here, everything out to infinity is in it. I pick any element out here, everything out to infinity is in it, but the line between them is not.
 So, this bizarre definition of these two things going out is a cone. This is at the origin, but it's not a convex cone.
 Now, to get a convex cone, you've got to consider what's called a conic combination. So, that means some gamma 1 and gamma 2 for all positive gammas. So, not just that one stays in, but everything, every combination, which is every line in between.
 Then you've got a convex cone. So, if it contains all of its conic combinations, it's a convex cone. We're focusing on convex cones, don't worry. I'm giving you an example just to say, it's not automatically convex, but in every situation, you're going to want to use it as a convex cone.
 Okay, and we will use cones. We'll see. In some cases, they simplify the notation. In other cases, they actually have some really important meaning for us.
 Okay, and the next one I want to talk about is a hyperplane. And a hyperplane is defined by this linear constraint. So, think of x as a vector, and it's the constraint A transpose x equals b.
 Now, when we're thinking about this, if I think in two dimensions, and I have, let me draw an axis, here, x1, x2, pick a point, here, and a vector, think of the vector A, as originating at some point, let's call it x, x0.
 Now, this constraint is essentially everything on the line that's perpendicular to that. And you can see that by taking any x on this line, the fact that it's perpendicular to A, which you can see it is here because I have a right angle here, if you believe my drawing,
 the fact that it's perpendicular means that the inner product between this line and A is 0. So, I could write that as A transpose x minus x equals 0, or A transpose x equals A transpose x0, and A transpose x0 was what I was calling b over here.
 So, everything that's on that line is in this hyperplane. Now, it's a line in two-dimensional spaces. In n-dimensional spaces, it's an n minus 1 dimensional subspace in there.
 So, the hyper, this A, which is actually also called the normal vector, removes the dimension and just defines down one dimension lower. So, in three-dimensional spaces, you've got a plane defined.
 Okay, that's a hyperplane. A half-space is everything on one side of it. So, here it's less than or equal to, and that would be everything in this region.
 Okay, and hyperplanes are obviously convex because any two points on the line, obviously, all points in between them are also on that line. And also, for the half-spaces, any two points in here, certainly the line between them is also in there.
 So, these are both convex. So, those are some basic convex sets, and those are the obvious ones. Let's talk about a couple more, and one I mentioned last, are what are called norm balls, and those are basically everything within a certain radius of a point.
 I'll say xc is some central point in there, and everything of a certain radius, and you measure that radius in terms of a norm. Now, you've got many choices of norms. Any norm that you have, you can define the norm ball, so it says less than r.
 And what's called the unit ball is, of course, just taking the radius equal to 1. And now I've shown some common ones in R2, so just on the plane here. So, the circle in green here is the one we normally think of as a sort of unit ball. It's the 2-norm. It basically describes a circle.
 So, everything inside that green circle, that's the 2-norm ball, or Euclidean norm ball.
 And I was talking last Wednesday about the blue one, which is the 1-norm ball. So, everything in that diamond shape, blue, satisfies that it has a 1-norm less than or equal to 1.
 So, here we've got the 1-norm ball. And, of course, the 1-norm of a vector is the sum of the individual components. 2-norm is the sum squared. 3-norm would be the sum cubed. It just goes on like this.
 Or, the sum of the absolute value cubed, I should say. You don't count the minus signs ever. And the infinity norm is when you take that limit, and actually you just get the maximum element. So, the red one is the infinity norm. So, the infinity norm is just the maximum magnitude component.
 So, maximum magnitude component less than 1 means either x2, or both x2 and x2 have to be less than 1, so I get that squared. So, those are 3-norm balls that we have. And they're pretty good.
 Now, once you have a norm ball, you could define, also now, combine it with a cone and get what we call a norm cone. And there you've got another parameter. You've got the vector x again, but you've got some parameter t, and you want to define the region where the norm of x is less than t.
 And, of course, you can choose any norm you want, and you can see you get this sort of shape here. I've shown the 2-norm cone in here, because this is a circle. So, it's the same circle that we have in green there. It starts at the origin, right down at the bottom.
 It always includes the origin, it goes to infinity, and it's sort of everything inside that. This is the ice cream cone I was thinking of. So, here you have, it's a convex conic one. Now, if I had said strictly equal to there, I would still have a cone, but it wouldn't be convex. It would really be just the piece I've drawn, really just the ice cream cone, no ice cream in there.
 So, this cone we use a lot as well, and it has a special name. It's called the second order cone.
 And, in the next day or two, we're going to look at something called basically conic optimization problems, where you constrain your variables to lie in cones in there, rather than you think of, I have a variable x, I want it to lie in a cone. You can write down optimization problems and solve them that way.
 I might be asking a bit too soon, but what is that useful for?
 Well, I can give you a trivial one. Suppose I want all my variables to be positive in there. I could say that it lies within the positive orphan, which is a cone. So, I could just write it lies in that cone. That's pretty much notation, because you could write it down and solve it just by saying I constrain it to be positive.
 But, we're going to get to the next slide, another cone, which is not so easy to handle that way.
 But, anyway, this is the second order cone.
 Another one, and this one is very useful, is what's called the positive semi-definite cone.
 And so, let's say S to the nth power are symmetric n by n matrices.
 Now, S n plus are all the symmetric matrices that are positive semi-definite.
 Now, positive semi-definite has a couple of equivalent ways you can write that down.
 What that means is, for all x, x transpose is greater than or equal to zero. That's positive semi-definite.
 Or equivalently, all the eigenvalues of x are greater than or equal to zero.
 So, both of those are characterizations of a positive semi-definite matrix, capital X, in there.
 Positive definite means it's strictly greater, and so you would just have x transpose x, x strictly greater than zero.
 Or all the eigenvalues of x also strictly greater than zero. That would be this case here.
 And those are cones, in there, and they're convex cones.
 And you can write down your optimization problem, and almost from today onwards,
 we'll be writing down optimization problems, not in terms of variables, but in terms of cones, in there.
 And this one, the particularly valuable one, this is the one that forms the basis of linear matrix inequalities, this cone.
 The positive orthon, you could say, is the way we do linear programs.
 Have you done linear programming in this class?
 There's some yeses and some noes, and the fact that Jeremy's going, not really.
 So you probably haven't done it in detail, but that is essentially programming over the positive orthon cone.
 LMI's program over the semi-definite cone.
 Okay.
 It's also convex with respect to the individual components.
 So here, if you think of this, this is a symmetric matrix, x, y, y, z, in here.
 There are three independent elements in there.
 It's symmetric, but obviously for not every choice of x, y, and z,
 is it going to be positive definite in there?
 But if you plot the regions where it is positive definite,
 and here I've plotted them against x, y, and z,
 you get this, I don't know what you'd call that,
 sort of like a hull of a boat type shape that comes out, which is convex.
 I've just shown the boundary of it where it would be equal to zero,
 but it is convex in here.
 So this is a convex cone.
 You can start drawing lines, you can go out to infinity,
 and you can get all conic combinations in there.
 Okay, so this example illustrates a couple of other interesting things.
 If you're just thinking of coding this up,
 one way of writing this is to write it as x times the matrix 1, 0, 0, 0,
 plus y times the matrix 0, 1, 1, 0,
 plus z times the matrix 0, 0, 0, 1.
 So now you've got three variables, x, y, and z,
 each multiplied by a matrix, but this is what you get.
 Someone who wrote the underlying code and a lot of the software that we use
 split this up as a characterization of positive definite matrices,
 and they code it individually like this.
 But we can write it down like this, consider it a cone,
 and you'll see that we can pass it to programs just characterized as a cone.
 Now internally, by doing this and recognizing that this is a convex combination in there.
 I think you've already seen this code called CVX.
 Not seen it yet? Okay, we'll see it maybe tomorrow.
 But it's sort of like a programming language,
 works in MATLAB, where you can more or less just say,
 this matrix, let's call it P, call that matrix P,
 and I can just say, define P as a semi-definite cone.
 Like defining x as a real variable or a matrix or a vector,
 whatever it is you want in MATLAB,
 you'll find that it defines another class called semi-definite matrices.
 And you can start programming just like you can in MATLAB,
 multiply them by other matrices, add them together, subtract them,
 test their positivity.
 And so you find that you're thinking of whole matrices as variables.
 I guess you'll code in MATLAB anyway, is that right?
 No, even that's dubious.
 Okay.
 Okay, actually, you know, there's a good reason for using Python.
 MATLAB's really pretty smart, although MathWorks is pretty smart,
 is that the licenses for MathWorks universities are free,
 but anyone who works in the company knows that they,
 well, in the U.S. there's about $10,000 U.S. dollars per license per year.
 I don't know, does anyone know, what's the price in New Zealand?
 $30,000.
 $30,000, yeah, okay.
 And so everyone who uses it in universities uses MATLAB
 because you get it for free, and it's got all this great stuff in it,
 and then you go and work in industry,
 and they say, whoa, no, you have to learn Python.
 So anyway, I'll write down stuff in MATLAB
 because I've spent 40 years thinking,
 oh, I should really get going with Python
 because it's much more useful for students who go into industry,
 and I've kind of never been happy.
 I've been too lazy to do that.
 So my apologies, but I'll sort of write it down in MATLAB.
 But Python's not so different in some ways.
 And actually, CVX, the code I'm talking about,
 has a Python library as well.
 So you're good.
 All right, so those are cones.
 Now, convex sets, again, I've given you some examples of convex sets,
 but one thing to think about or create more complicated things
 is that all intersections of convex sets are also convex in there.
 So if I've got one convex set like this,
 another convex set like this,
 then this intersection in between,
 that's pretty weird, isn't it?
 That's also a convex set.
 So you can build up more and more complex convex sets.
 So, for example, think of this as a constraint
 where X is a vector, C is a matrix,
 and it's an equality constraint.
 So each row of this,
 so think of CI, this CI bullet,
 maybe I should have said CI colon if you're into MATLAB,
 but think of that as a row of C
 multiplied by X is some component of B.
 So each one of those lines is a hyperplane.
 And so what I have here is an intersection of hyperplanes.
 So you can think of a line going through this way
 and a line going through this way,
 and point is a convex set,
 and it's a pretty boring convex set,
 but it is a convex set.
 In higher-dimensional spaces, in three-dimensional spaces,
 you get two hyperplanes, you intersect, and you get a line.
 But you'll always get a convex set.
 If you do an inequality,
 then it's a little bit more interesting,
 because now you've got half-spaces,
 and now you've got intersections of half-spaces.
 And so you might have a line here,
 which defines a half-space on one side,
 another one here, another one here, another one here,
 and so the space you're defining in the intersection is this.
 So each one of these might be defined
 by a normal vector and a point,
 and so you define a sort of polytopic region.
 Now, this is useful in a lot of classification problems.
 Does something have this particular property
 or for defining sets in there?
 So these are intersections of half-spaces.
 They're also convex in there.
 There's actually two ways of thinking
 about how you would define this intersection,
 or how would you define that set?
 Another way you can define it
 is to define it by vertices,
 and then say that it's the convex combination of the vertices.
 Everything in the middle
 is a linear combination of the corners in there.
 That's another equivalent way
 of defining a polyset like that.
 And theoretically they're the same,
 but numerically they can be quite different.
 Solving things in terms of half-spaces can be easy
 when the same problem in terms of vertices is had,
 and vice versa.
 So, for example, if I want to check
 if a point is in my half-space,
 all I have to do,
 or so in this intersection,
 I have some point and I wish to test it,
 I just have to check that it satisfies
 the half-space constraints of my four.
 So I do four calculations, four inner products,
 and if it passes all four tests, it's in there.
 Now, finding, say, the smallest ellipse
 that contains that set
 is a problem we'll talk about today.
 Finding the smallest ellipse
 is fairly easy in terms of the vertices.
 It's NP-hard in terms of the edges.
 So whatever problem you have,
 these two representations are the same set,
 but the characterization can make the problem easier or harder.
 But anyway, it's a convex set.
 There are a couple of different characterizations there.
 So in general, you can think of polyhedra
 as being defined by AX,
 an inequality in here,
 and possibly some linear equalities
 slicing it down to a lower dimensional space.
 All right, so those are convex sets.
 And I'll give you one example here,
 because we'll use this one today
 and extensively later,
 and those are ellipsoidal.
 And so I've, pretty much I gave you
 a little picture of one before,
 but an ellipsoidal region is defined
 by this constraint here.
 Now, this is a quadratic constraint.
 Now, that matrix P in the middle,
 I've written there in terms of P inverse,
 P is going to be positive definite matrix,
 all positive eigenvalues.
 And then what we have
 is some ellipse
 with some center point XC here.
 And the difference,
 when the difference,
 it's sort of like a weighted norm difference
 between every point in this set,
 and the origin being less than one,
 where P inverse just scales it.
 So then in different directions,
 you get different characteristics.
 You can go further before you hit one,
 say that direction there.
 So that's an ellipsoidal region,
 and that's the center.
 So checking that the vertices are inside that,
 so if I had some polytopic region before,
 and I wanted to know,
 does the blue box, or the blue rhombus,
 sit inside,
 then I can take all four corner points
 and just plug them into that thing,
 just do X minus,
 take the X minus XC,
 P inverse, work that out,
 see if it's less than one,
 all four paths,
 then it's certainly inside the ellipse.
 But if I actually specify that region
 by my half spaces,
 it's very, very hard
 to figure out
 if the intersection of those half spaces
 is inside the blue ellipse.
 And in fact, it's combinatoric.
 So the calculations you have to go,
 go to the power of two
 to the number of points you're trying to check,
 edges you're trying to check.
 So that's ellipses
 that are a very powerful convex set
 that we'll certainly work a bit more with.
 Okay, so those are convex sets.
 You've probably seen convex functions in here.
 So essentially it's a function,
 again, satisfying the same rule almost.
 So that if you have two values of the function,
 then the line between them
 lies above the function.
 It's convex.
 So it has a curvature like this.
 So the line in between these two points,
 and so I've got the point X and Y,
 and I look at the,
 this is the line between,
 so this line down here,
 and that's greater than or equal to
 every point evaluated
 along the linear combination of X and Y.
 So that's a convex function.
 And the domain of that function
 we assume to be a convex set.
 That's why I started off talking about convex sets.
 So you define your functions on a set.
 And that set has to be convex.
 You could define a function that has this property,
 but it's on some weird domain.
 It's maybe split in two pieces or something like this.
 Then that's not a convex function
 because it's not defined on a convex domain.
 So we want it to be defined on a convex domain.
 And it's concave if it's negative is convex.
 I'm sure you know that.
 And I could talk about strict convexity
 or strict concavity by just
 replacing the less than or equals
 with a less strictly less than in there.
 So a strictly convex function is always curving.
 But one that's just convex
 could have a flat region in there.

 convex functions,
 and
 convex functions have, you know,
 the nice property you've already seen, I'm sure,
 is that if you minimize them,
 you'll get the global minimum.
 Strictly convex functions have a unique global minimum in there.
 Okay.
 And so this is the basis of convex optimators.
 I'll give you some examples here.
 So for a convex function,
 for example, affine functions,
 any line is convex.
 It's even stronger than that.
 Exponential functions,
 e to the ax.
 Now notice here I'm being a little bit careful
 to define what the domain is
 because we have to be sure that the domain is a convex domain in here.
 So here I'm looking at a function x
 for any real, you know,
 the whole line is the domain here.
 Powers x to the alpha
 on r plus plus.
 So in other words, I'm only considering positive x.
 Strictly positive x.
 So here what I mean is x is strictly greater than zero.
 And if I choose alpha greater than one
 or less than zero,
 then I have a convex function.
 But there's a gap missing,
 so I've got to have one definition or the other in there.
 If I consider the whole number line,
 there's a piece missing out of the middle
 where it's not convex in there.
 So I can say I have a convex function
 for negative alpha
 and a convex function for positive
 greater than one alpha
 but not in the middle.
 Powers of the absolute value
 x p
 p greater than one
 and you can see that that really works because
 there we're simply talking about norm balls.
 The p-norm ball is
 is basically
 sorry, let's rub that out.
 x to the power of p
 and p goes from one up to infinity.
 So you can see that they're convex
 in there.
 Negative entropy
 in there if you enter
 that is x log x
 on positive, strictly positive values of x.
 Now you can see on negative values of x
 you get a problem with defining log x
 so we restrict ourselves to strictly positive x
 in here.
 And x log x is actually convex.
 Okay, concave functions
 just to give you some examples.
 Affine functions, note
 they're both convex and concave
 because they're in a straight line
 they don't curve at all.
 So they fit both characterizations.
 Powers, again,
 but this time only for alpha between zero and one.
 The other parts we know to be convex
 that part is concave
 and also the logarithm
 log x on x greater than zero
 because log x goes up like that.
 And interestingly enough
 if you just multiplied it by x
 it's enough to tilt it the other way
 because x log x is
 convex in there.
 So those are some examples
 you've probably seen most of the examples
 whether you've thought about them as convex functions or not.
 These are what you have.
 Okay, so
 let's do convex optimization.
 We can think of looking at
 well, convex functions
 and higher dimensional spaces.
 All of these examples I gave you here
 are just on the real line.
 So all of these cases
 x was just a real number.
 Let's think of x as a vector now
 on Rn.
 And again, you can write affine functions
 but now, of course, because x is a vector
 you've got a and b are vector values
 in there.
 But it still has the property
 you need two points.
 Actually, these ones are on the line.
 Norms are convex functions.
 P-norm
 is exactly those
 balls that I drew for you before.
 So there you have
 take the magnitude of each component
 raise it to the p-th power
 take 1 over p
 the p-th root of it
 in there.
 So
 p equals 3
 cube roots, which we'll try later
 in there.
 Those are convex functions.
 But on vectors
 now your domain is in vectors.
 You can even go, of course,
 to look at matrices.
 You might decide on square matrices
 symmetric matrices
 or even general
 n by
 m by n matrices, so non-square
 matrices. You can still have all
 of these things.
 So one example
 the affine one again
 both convex and concave
 the way you define that
 is the trace of a matrix
 a times x.
 So the trace is the sum of the diagonal elements
 and you multiply
 it by a matrix. That's an affine function.
 So it's like ax
 plus b but in the matrix space
 in there. So you can
 see what it is if you write it out in terms of the

 Other things are actually
 norms of matrices.
 So the 2-norm
 of a matrix is the maximum
 singular value. Are you familiar
 with singular values?
 Okay, good.
 That's good.
 Important stuff.
 And so the maximum singular value
 is actually the square root of the
 maximum eigenvalue of x transpose x.
 But that's also a convex function.
 So all of these
 are convex functions
 but I want to just get the idea that we might
 be considering domains which are not just x
 as a real number.
 We'll be defining
 our functions as either
 vectors or matrices
 and then trying to optimize, say, to find
 the best vector or the best matrix
 in there. Now someone who wrote
 the code deep down is dealing with
 individual elements of xij
 in the software
 but if you're using, I guess, a library
 in Python or you're using
 MATLAB, that's abstracted away from you
 and you can just write in terms of the variables
 x in there
 which saves you a lot.
 When I was a student, we couldn't
 think in terms of the variables x.
 We had to code
 thinking this way. And actually we had to do
 it in assembly language
 in this. So it was a bit more painful.
 I was
 probably in about the second or third
 year of my PhD when MATLAB
 came along.
 That was groundbreaking that we could
 think in terms of matrices and vectors
 and just write out the equation.
 And the calculations were automatically
 done.
 So
 anyway, convex optimization
 for that.
 Another thing which is useful for a lot
 of problems, particularly in control systems
 are quasi-convex functions.

 they're not quite convex.
 Well actually they're often not convex
 but they satisfy some
 of the
 properties of convexity.
 And
 we'll call a function quasi-convex
 if the domain has to be
 convex, so it has to be defined on
 a convex set, a real line
 or matrices or
 vectors, but convex
 sets, and has the property that all
 sub-level sets
 are convex.
 Now a sub-level set
 if you take, so here
 I've got a function here.
 If you draw a line through the particular
 value alpha
 here, and then you look
 at the set that's below alpha
 that's the set
 from here to here
 that set is convex.
 And you can see that's true
 but you can check it for every
 line I drew across
 the set is still going to be convex
 in there.
 And so, yeah, that's called a sub-level set
 and you're quasi-convex
 if every sub-level set is convex.
 Now you can see this function's not convex
 but it gives you a way
 of solving it. Gradient descent
 will sometimes
 work, but it might
 get stuck where things go
 flat. Flat doesn't mean you're at the bottom
 in here
 when it's quasi-convex.
 So a better way to do it
 for quasi-convex functions
 and this can be generalised, is
 to characterise the set
 that satisfies
 I didn't draw my
 set very well, did I?
 It shouldn't be there, it should be
 there.
 Hopefully that's not a confusion
 for you. But anyway,
 what you do is you pick
 a value of alpha and you
 characterise this set
 here
 and then
 you can
 say, OK, I know that between here
 and here is the minimum.
 Because notice the sub-level sets
 are by definition nested.
 You know, if it's a sub-level set at one level
 it's definitely at a lower level as well.
 So now you have to pick
 a lower one. One way to pick
 is to take, say, the midpoint
 of this set, evaluate
 the function, and now
 look at that sub-level set.
 That actually
 is called bisection.
 It pretty much does that. And then, so now
 you've got a new sub-level set and you pick the middle
 of that and then look again.
 So you can always get yourself
 down to this
 if you subdivide
 enough times.
 So you can find the global
 minimum. They have
 a global minimum
 if you find the minimum of the gradient
 being strictly positive in every direction
 away from it.
 They have a global minimum
 and you can find it by bisection.
 So all of the nice properties
 you were looking for in a convex function
 you have to modify your algorithm a bit
 and think about it a little bit differently
 but you can get to the global minimum
 of a quasi-convex function
 just by bisection.
 And some functions
 are quasi-convex.
 Okay.
 So
 for optimization with
 convex functions, I want to
 define a rough standard form.
 We'll in general
 be minimizing some function
 F0 I'll call it
 and there'll be some constraints
 and there'll be a mixture of inequality
 constraints
 in general
 or equality constraints.
 And you can see
 whether I've got less than or equal to or strictly equal to
 in this case we'll get one or the other.
 Okay.
 But there are some caveats
 in here.
 If I want this to be
 convex, and I can't remember if I've got this
 on the next slide or not but in case I haven't
 I need to have
 this set
 these two characterizations
 here define what's
 called the feasible
 region
 here and of course this is the
 objective function
 So I need
 the objective function to be defined
 over at least
 all of the feasible region
 otherwise it's not making much sense
 and I need that feasible region
 to be convex
 and I need the objective function to be convex
 and I have a convex optimization problem
 Although we'll actually
 restrict it
 we'll look at different classes of problems
 that's just a very general idea
 of what the problem is but we'll look at some different
 particular forms
 So a few things to think about
 So what I want to do
 actually, so that's a general convex
 problem. I want to introduce you very
 briefly in the next 10 minutes
 to an algorithm that can solve
 almost any convex or quasi-convex
 function problem
 in there. And it's an algorithm
 which you can probably write in
 10 to 12 lines of code
 So
 and
 okay
 Let me
 just to set it up, think about a few things
 So here's our
 standard form that we're
 going to look at. I'm going to minimize my
 function, I have some inequality constraints
 The equality
 constraints I'm going to assume are all affine
 If they aren't
 actually what I can do is I
 can make
 nothing on linear equalities
 by subtracting one side from the other
 and putting in a slack
 variable, I can put them into
 this bunch
 and then make the slack variable
 equal to zero on this bunch
 So
 it's still fairly general
 Now my domain is obviously the
 intersection of the domain of all of those
 and I'm going to assume I can eliminate
 the affine
 constraints
 So this is usually
 pretty easy to do
 So you have this x
 and x has to satisfy these
 constraints here. You could write that as a matrix
 equation where you have a particular solution
 x zero
 and then f of z
 defines all of the other ones that
 x can
 satisfy. So let me
 put it this way. If I
 wrote this constraint as ax
 equals b, where the ai
 are each row there
 then what I have here
 is
 A F
 Z
 plus AX_0
 equals b. So you can see
 my X_0 has to be
 one solution for this
 and af equals
 zero. So this characterizes
 the null space of A
 of A
 So just to eliminate
 it's really just a matrix way of
 writing down what you would probably do anyway. You have an
 equality constraint, you solve for the variable
 and you substitute it back in
 And you've got some degrees of freedom
 in the f times z
 when you solve for the variable
 If you don't have any degrees of freedom, then x zero
 is the answer and you're done
 But in general it's not
 the answer and you've still got to do some
 optimization
 Okay, so let's parameterize it
 into a matrix phi of z
 So I've taken away the inequality one
 and I just have inequality constraints
 psi
 of z
 So what I've done is I've just put that
 solved the linear equation
 just to get all possible
 linear solutions and then substituted it in
 And so this is the idea
 And it's going to go back to
 this idea of ellipses
 So let's say
 I start with some huge ellipse
 and I'm pretty sure
 that my minima is somewhere in this
 ellipse
 So what do I do
 is at the center
 of this ellipse
 I evaluate
 the cost function, phi
 and the constraints
 psi
 So I get the constraints
 in the cost function there
 Let's just focus for the time
 being on just the cost function
 Let's say we haven't got any constraints
 What I do
 is I use the gradient
 or sub-gradient information
 You know what a sub-gradient is?
 No?
 So in functions where
 they're not differentiable
 So maybe, if it's differentiable
 you all know what the gradient is
 But if it's not differentiable
 So you have a kink in some function
 like this, where at this point
 here you're not differentiable
 The sub-gradient is the set
 of all
 lines that still
 go underneath
 So you replace the gradient with a set
 of gradients
 And those are called sub-gradients
 They're still under the function
 But now at this point here
 they're not unique. Now everywhere else
 you've got one gradient
 But at some points you may
 not have. So you can
 use the sub-gradient or the gradient
 whatever you have. And now
 because it's a convex function
 if the gradient points this way
 you know that
 if you take the ellipse
 and cut it in two
 then
 the minimizer has to lie
 in this one
 Because the
 contour lines, they hit this
 point, they all curve inwards
 because they're convex
 So any
 sort of contour functions you have
 are doing something like this
 in here
 So
 you know that everything
 up here
 can't have the minimizer
 It has to be down here somewhere
 So what you do
 is now that it's down there
 or you know it to be down there
 you draw
 the smallest ellipse
 terrible ellipse, sorry
 you draw the smallest ellipse that contains that half
 ellipse
 And now what do you do?
 Back at standard, evaluate the cost
 again, and you end up with these ellipses
 that shrink as you go
 step by step, and you go smaller
 and smaller. And actually the amount
 it shrinks
 is easy to calculate
 it depends on the dimension of the space
 in there
 but it shrinks a certain amount, a certain percentage
 every time you do this
 The other thing that's nice is this
 green ellipse here
 actually has a closed form solution
 I'll write it down for you in terms of three equations
 that you can code up
 there's three of your coding lines
 in there. So you can
 do that and then you say okay
 start again, and each time it's the ellipse
 that contains the solution goes smaller and smaller and smaller
 and also sometimes
 it adds in some areas that you didn't assume
 to be there, but it doesn't matter
 it contains it. And actually it might be
 useful if you're slightly wrong and the point was
 actually out there, then it would capture it again
 so it could be useful
 Okay
 so the idea with this
 is called a cutting plane
 and so
 here's your ellipse
 at iteration k
 and I've got a
 gradient, it could be a sub-gradient
 then here is the half-space
 that I know contains the minimizer
 so that's exactly this half-space
 I've shaded in, well this half-space
 here
 and then what I need for a new ellipse
 is that it has to be the intersection
 of the old ellipse and the half-space
 and
 this is what you do
 so here is your calculation
 you normalize the gradient
 with respect to p, because you only care about
 its direction, you don't care quite how big it is
 you get g tilde
 this formula gives you a new ellipse
 center, if this was the old one you
 adjust it, notice
 the scaling depends on the dimension you have
 and this is the new p describing
 the ellipse, a little bit complicated
 but it's
 basically it's a rank 1 update to the old
 p
 and then you're guaranteed
 to go down in volume
 by e to the
 minus 1 over 2n
 so if n is 2 on the plane
 the volume drops by 77%
 at each step
 and actually
 this set of calculations
 were used to prove
 that linear
 programs complete in polynomial
 time, in 1984
 this was a big deal
 and so it was basically
 the ellipse
 calculations that showed this to be the case
 so that this guarantee
 means that you converge to a certain amount
 pretty quickly
 so one way you can think about
 stopping this
 is if you've got one center and you evaluate
 it
 and you think, what you're doing
 is you've picked your center, you've got a gradient
 if you take that gradient all the way
 to the other side of the ellipse
 you know it has to be
 a function, because it's a convex function
 and this is the distance to the
 other side, evaluated
 so you know, this is how much you can
 go down, going to the other side
 So you get an upper and a lower bound.
 Your upper bound is the evaluation of the centre,
 and your lower bound is projecting that along the gradient
 until you hit the other edge of the ellipse.
 So you can keep track of your upper and lower bounds,
 and when they're close enough, you stop.
 I'm done.
 Okay, one quick thing that will take hopefully a minute.
 Constraints.
 So you've got a constraint there.
 You've got to satisfy these constraints as well.
 What you do is you use the constraints.
 Okay, if these constraints are convex set,
 if I evaluate the gradient of all the constraints
 and one of them is positive, so it's not satisfied,
 I know I can throw away half an ellipse.
 So you throw away any part of the ellipse
 where the gradient function evaluates to a positive number.
 Chuck it away.
 So you can do even better than that with what's called a deep cut.
 Okay, anything that throws away pieces of ellipse is useful for you.
 So what you do is suppose you evaluate the constraint function here.
 So psi 3 of this xc was equal to 10.
 Okay, it's greater than zero.
 So this region's not feasible in here.
 This is not feasible, but actually it's not that close to being feasible.
 It's supposed to be less than zero.
 So what you actually do is you go back along the line of the gradient.
 Let's say this gradient went that way.
 You go back along the line of that gradient for this distance
 because this would be using that gradient information
 to at least get a bound on where it's going to hit zero.
 And you say, ah, okay.
 If it was a line, it would hit zero at this point,
 but it's a lower bound, so it might still be above zero,
 but I know for sure that this point is not feasible right at zero,
 or it's right on the edge,
 so I will now instead just look at the ellipse in that region.
 And what this here is known as, that's the deep cut.
 Okay, if you cut off even more.
 So the constraint function, you can do that.
 With the cost function, objective function, you can't really do that.
 But constraints.
 And so you just check.
 And one thing to do is to evaluate all your constraints
 and then see which one would give you the deepest cut.
 And use that one and then chuck it away and keep going.
 So now this converges pretty quickly,
 and I'm showing you all the equations you really need.
 Not quite to do the deep cut.
 You'd have to work out a little bit there.
 But I've shown you the equations you need to code it up.
 So you probably can do it with 10 to 15 lines of code in there.
 So anyway, that's one way of solving any convex problem.
 It's not the most efficient way,
 but the most efficient way will lead to some of our postdocs
 who work on it all the time
 and then release the code into the public domain.
 And we'll talk about an example of that maybe tomorrow.
 But anyway, that's how you can solve those.
 I mean, it's kind of fun.
 Well, maybe you don't think this is fun.
 But, you know, if you do think it's fun,
 you're looking for something to do,
 try and code up the ellipsoidal algorithm,
 even just the unconstrained case in there.
 And you already have all the formulas you need.
 Okay, are there any questions?
 Before we get into some actual real stuff tomorrow.
 This is just sort of setting up the notation.
 All right, see you tomorrow.
 Thank you.
 All right.
 Okay.
 Yeah.
 Yeah, okay.
 That would be great.
 Thanks.
