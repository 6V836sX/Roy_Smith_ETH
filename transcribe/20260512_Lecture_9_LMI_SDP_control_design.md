 Okay, let's begin. I think we're recording. And before I begin I want to ask if there are any questions, technical questions or whatever.
 Okay, let me start. So this I guess is part 2 or lecture 9. Notice my numbering is not coherent.
 But basically we're talking about linear matrix inequalities or LMIs today.
 So let me begin and I'll start from more or less where I left off yesterday which was describing convex optimization problems.
 Okay, so there's a whole family of convex optimization problems and so I'll go through the taxonomy of this family if you like
 and talk a little bit about the different problems.
 So the simplest one, which is the simplest one to write down at least, are linear programs.
 And these are quite simply having everything linear.
 So you've got a linear objective in there or it might be affine. Technically fd is not equal to 0 but we call it linear.
 So there's a linear cost function. You've also got linear inequality constraints here, a variety of them.
 You can stack them up into a matrix form. And a linear equality constraint.
 So all of the things are in there are linear.
 So the feasible region is described by these linear constraints and as I talked about yesterday that gives you polytopic feasible regions in there.
 And a linear cost. So one way of thinking about this is sort of the picture, if you like, the contour map would be some sort of polytopic region, say, in space.
 Let me trim off its edges like this.
 So there's some polytopic feasible region and the contours of the cost function would be some line.
 So you can think of contour lines like this and maybe decreasing is this direction.
 And so the solution of this linear program, of course, is going to be this point here right on the edge because the contours go down there and you hit the edge of the region.
 Now, linear programs, generically, you hit the edge of the boundary.
 The vertices are this. One of the vertices is the solution.
 And then it's a question of finding which one it is.
 You might, if you had exactly the right contours, you might actually hit a whole edge, in which case you have a non-unique solution.
 But a lot of the algorithms, early algorithms for doing this would run around the vertices, basically looking for the smallest one.
 There are rules for keep going on the direction from this vertex to the next one in the direction where you're minimizing the cost as you head along.
 So there are lots of ways of doing that.
 And I pointed out these things usually ran in polynomial time.
 In other words, the time it took to solve the problem was a polynomial function of the number of vertices you had there.
 But proving that was, you know, this was sort of observed and known from the 1960s, but proving it didn't come until 1984 was sort of the algorithm.
 But anyway, that's sort of the simplest form, linear programming problems.
 And there are a lot of problems that come up in this way.
 So, the diet problem is sort of one of these.
 So this is the problem where you say, I've got a dozen different food groups.
 That'll be caffeine, alcohol, ice cream, you know, the stuff you really want.
 And you might have some potatoes somewhere down at the end.
 And for each one, you can say it has a certain amount of calories, it has certain content for nutrition, a certain amount of fat.
 And so you say, if I want to get my total calories for the day between some minimum and maximum value, which is reasonable,
 and I want to satisfy bounds on the amount of nutrition, upper bounds on the fat, lower bounds on the nutrition, if you like,
 then all of those are just linear constraints.
 You know, the sum of the calories in the individual parts.
 Your X variable is how much of each thing to have, how much of each food group you want to have in your diet.
 So that's not only the diet problem, but this actually generalizes to all sorts of things in logistics problems, delivery.
 So, you know, they use linear programs to figure out how much of each thing they're trying to sell goes to each supermarket,
 depending on what they estimate the demand will be.
 So a lot of these problems are quite simply linear programming problems.
 Another one, which is also finding the Chebyshev Center, that's the largest ball inside a polyhedron.
 So I think we can probably understand that problem now from the point of view of what's the largest circle you can fit inside there.
 Also a linear programming problem.
 So anyway, those are the typical examples.
 Linear programming has been around for a long time, and there's a very efficient code for solving it.
 So a lot of these problems are sort of logistics, allocation-type problems that come into linear programs.
 Okay, quadratic programs.
 What's called a quadratic program just has a quadratic cost function to it.
 But the polytopic feasible regions are still the same.
 So we're going to assume here, well, people describe this as a quadratic problem,
 but you still have a feasible, which is set by linear constraints.
 So again, you're looking still at polytopes like this, but now your contours are curved.
 And the curved contours might mean that you don't necessarily end up at a vertex, as you would in a linear program.
 Maybe the minimum on this feasible set at this point.
 It's not quite at the vertex here, depending on how those contours line up.
 So this is a more difficult class of problems.
 The most obvious one is one we've already seen, and that's least squares.
 Minimize the cost.
 So remember phi theta minus y, 2 norm squared.
 That's exactly a quadratic constraint in there.
 And you might actually put bounds on C.
 So there might be some lower bound L on theta, sorry, and some upper bound U.
 You say you want it to lie between these bounds, so constrained least squares.
 Now constrained least squares doesn't have a closed form solution like the normal equations,
 but it's still a quadratic program, and it's fairly easy to solve.
 So linear least squares, or constrained linear least squares are problems that fall in that class.
 Portfolio optimization.
 If you think of how much money you should invest in which shares, with limits on how much money you have.
 Let's say maybe that my upper bound on the total budget is pretty small.
 But those are polytopic constraints.
 And if you think of what's your risk when you...
 I think this turned off.
 If you think of what's your risk when you're doing this,
 you could make the risk proportional to the variance, the expected return.
 There's a suspected variance, and that variance comes in, of course, as a quadratic term.
 So that's another one.
 The third one, which often falls into this category, is one form of model predictive control.
 In other words, you use optimization for your control system.
 And this is used in a lot of places.
 And I will spend all of tomorrow talking just about that.
 And probably run out of time anyway.
 It's a big topic.
 So we have master's courses in Zurich.
 That is the entire focus.
 Oh, I can compress it down.
 Don't worry.
 We'll see how that goes.
 But anyway, those are all quadratic programs.
 And there's some very good solvers available.
 So one of them is called OSQP, Open Source Quadratic Program.
 And that's written by some of the best people in the world at writing this sort of code.
 And it's publicly available.
 It runs in MATLAB, and you probably run it in Python, I'm sure, as well,
 just knowing who some of the authors are.
 One of the authors is a postdoc at my institute in Zurich, or was a postdoc.
 And another one was also there 10 years ago.
 He's now a professor in Oxford.
 And the third one is a good friend of mine.
 So it's a bunch of people I know.
 I trust their software.
 So I would say there's pretty good ways of solving that problem.
 Okay, now let's make it a little more difficult.
 So here I'm going to go to what's called a second-order cone problem.
 Now, we've talked about conic constraints.
 Think of this ice cream cone picture I had before.
 And those ones, we have essentially a linear cost in here
 and a constraint here, which you see is membership inside a cone.
 So the norm of some affine function is less than a linear function of your variables.
 And there might, of course, also be some equality constraints in there.
 So these ones have linear cost.
 Linear cost is, in a sense, universal.
 You see it written down.
 For a lot of these types of optimizations, we assume we have a linear cost.
 And you think, but hang on, my cost might be something else.
 It might not be linear.
 But the usual thing, especially if you've got some cost function J of X,
 which you really care about,
 and you think, okay, I want J of X, and maybe it's quadratic,
 maybe it's cubic, some bizarre function you've got in there,
 and you buy this software, supposing you paid for it
 instead of you didn't get the open-source stuff,
 you buy the software, and then what happens is
 it assumes a linear constraint.
 It's not linear.
 So what you do is you write down this minus some gamma less than or equal to zero,
 call that a constraint,
 and now your cost is just gamma.
 Minimize gamma.
 So what you're seeing here is this,
 this constraint just basically means that my cost is less than gamma,
 and then find the smallest gamma.
 And so this cost is linear.
 It's almost trivial.
 So often, this is called an epigraph method.
 You just say, I assume my cost is below that,
 and if I'm allowed to use this as a constraint,
 and often you can stick it in here as a constraint,
 then I can use my software I've paid for,
 which only treats linear costs.
 So these are called second-order cone problems,
 as I said, because this really describes a cone.
 It's a norm cone.
 Here's a bound here.
 It's exactly that ice cream cone, if you like,
 if this is describing the height of your ice cream cone.
 So now your feasible region, you can have more than one of these.
 I've got M of these constraints.
 These are intersections of second-order cones.
 It's a bit hard to imagine what that might be useful,
 but actually that's what you have in general,
 but it is actually fairly useful for some of these cones
 that we talked about yesterday.
 And the other thing is, quadratic problems can be posed
 as second-order cone problems as well
 by using this trick to get the linear thing,
 and now you've got a quadratic function here,
 but instead of a quadratic, you might be able to use a norm.
 So think of this example, least squares.
 Remember the cost function for least squares we had was
 the norm of the regress of phi, theta minus y,
 two norms squared.
 That was our least squares cost.
 But you get the same solution if you don't square it.
 It's still minimised at the same point,
 so whether you're minimising the square,
 which would give you this sort of thing,
 or whether you minimise the linear one,
 which would be this, because norms are linear.
 This property of a norm, you scale the variable
 and you scale the norm.
 So they're both minimised at the same point.
 So leaving the square off gives you exactly the same solution,
 and leaving the square off makes it a second-order cone problem.
 So this would give the same answer.
 Now, the reason we square it,
 or the reason Gauss squared it, for example,
 is you can differentiate it,
 and when you differentiate it,
 you get a nice linear set of equations to solve.
 Very, very beautiful.
 But with modern solvers these days,
 this method looks great, and theoretically it is great,
 but actually you can sometimes get more efficient solvers
 that actually treat it better as a norm.
 So it depends a bit on your solver,
 what code you're using to solve it,
 but if you go and look at CVX,
 they recommend that you don't put squared things in here.
 Where possible, you reformulate to get a norm
 in your second-order cones.
 Yeah?
 I was under the impression that a square to get rid of the...
 just not doing it at zero.
 That's true. That's also the case.
 Here, you've got a discontinuity at zero in this,
 but when you have this software,
 basically the way the software works is it does this.
 It sets a limit here, say some gamma,
 and then it characterizes the region
 where things are below gamma,
 picks a center point,
 and then projects it down to the cost function
 and keeps repeating it, so it narrows into gamma.
 And in this case, being not differential
 doesn't make any difference to it.
 It's just as easy.
 But if you're going to calculate a gradient,
 then, yeah, it's much nicer to have one
 that doesn't have a discontinuity in it.
 So that least squares method is great
 when you want to express it in terms of gradient,
 you want to express it in terms of normal functions,
 you want to minimize a Lagrangian,
 that's the right way to write it down.
 But actually, often in code,
 this is a better way of writing it.
 Depends on the solver.
 Read the manual, basically,
 and see which ones are recommended.
 Okay, there's another variation.
 We can keep making this more and more difficult here.
 Quadratically constrained quadratic programs.
 So this case, now we've got a quadratic
 both in the cost and in the feasible region,
 so both of them are there.
 And now the feasible region is the intersection of ellipsoids.
 Or lines, or hyperplanes, if you like.
 If the particular P for one of these,
 if P i was zero, there would be no quadratic term
 and you'd just have a linear constraint,
 which would give you a hyperspace.
 Or you could have a conic region as well.
 And as usual, we put in a linear constraint as well.
 So examples here are more stock market examples,
 optimizing your portfolios,
 but this time when the risks of the different stocks
 are correlated with each other.
 So if you invest in British Petroleum,
 and you've got a certain amount of risk,
 and you invest in Standard Oil,
 I guess that no longer exists.
 But you pick another, let's say, petroleum company,
 and they've got risks.
 These risks are not independent.
 All it takes is someone to close the Strait of Hormuz
 and then both of them either go up or go down.
 If you think they're going up at the moment,
 because fuel's getting more expensive.
 But the risks are correlated in there.
 So they don't go independently, they're correlated together,
 and so in more sophisticated portfolio problems,
 you often end up with a quadratic term from this correlation.
 Another one is also agriculture.
 It's used for deciding what crops to plant in what fields.
 And there your risks are, you know,
 weather, hurricanes, floods, whatever it is,
 but also the price that you're going to be able to sell it for.
 And these risks are also not uncorrelated.
 In deciding what to plant, you know,
 your beans are probably no more likely to survive your hurricane
 than leeks or any other thing.
 Except maybe rice.
 Rice likes flooding,
 but all of the others would not do so well.
 So there you get correlation between them
 and you get the same sort of effect.
 Okay, so now we're getting into, say,
 more and more complicated optimization problems as we go up.
 And I'm going to make another generalization,
 which I introduced to you yesterday,
 which is talking about what are called
 generalized inequality constraints.
 So rather than saying something's less,
 some function's less than zero,
 now let's think of our inequalities or inequalities
 in terms of vectors or even matrices.
 And we would like to say they lie in a cone.
 So the notation I'm going to use here
 is this.
 It doesn't come out very well on this font,
 but if you squint, my eyesight's much worse than you.
 You notice this is a curving, preceding, succeeding.
 It's not a straight line less than or equal to it.
 It has a curve on it.
 And so that notation I'll use for I mean a cone,
 not a function being less than or equal to a number.
 So, okay, the font for this is not so great.
 But so if I have a constraint
 that some function f of x is less than y,
 think of f as maybe it returns a vector,
 not just a number, but a whole vector,
 and y is a whole vector.
 If I have this conic constraint,
 what it means is y minus f is inside this cone.
 So take the y across to the other side,
 or take the, actually do it,
 you take the f to the other side,
 and you get y minus f,
 and greater than zero,
 and greater than zero means it belongs to your cone.
 Now your cone could be something like
 the positive orthant.
 I mentioned this yesterday.
 I said my cone is basically
 this whole region
 where variables are positive.
 Maybe x1, x2,
 everything's positive.
 And there, that's an easy thing to check.
 But the really useful one for us
 are these semi-definite cones.
 So now to think about
 a semi-definite conic constraint,
 f has to return a matrix.
 Actually, it has to return a symmetric matrix.
 Y is a symmetric matrix.
 And now what you'd like is
 y minus f is a symmetric matrix,
 but positive semi-definite.
 So that's what it means to be lying in a cone.
 And so this makes this idea of
 an inequality constraint a little more general.
 It's not element by element.
 The positive orphan is pretty simple.
 It really is each element is positive.
 But positive semi-definite cone
 is much more complicated than that.
 It's not the same as each element being positive.
 It means your symmetric matrix
 has all positive eigenvalues.
 So the fact that you can write that down
 as a single constraint
 in an optimization problem
 lets you have much more generality in there.
 Well, it wouldn't do any good
 unless you could solve it as well, right?
 But we do have code that solves
 optimization problems written in terms of cones.
 So that's why I'm introducing this.
 And so let's look at this idea
 of generalized constraints a little more.
 So here we've got some cost function in there.
 Again, assume it's a convex cost function.
 And now I've got a conic constraint.
 So here's my conic constraint in here.
 And again, I might have a linear one.
 So there's another form of problem
 called a conic problem
 where we have a linear cost.
 But as I pointed out,
 that's fairly general in that.
 But now we have this one cone constraint here.
 X could be a matrix,
 in which case F and G would be matrices in there.
 Or X might be a vector,
 in which case F is a matrix
 and G is a vector in there.
 But that's what's known as a conic problem.
 And then the last generalization I have here
 is that you replace that conic problem
 with a linear combination of these.
 So here we have, again, a linear cost.
 But now we have this form here.
 And so it's our optimization variables.
 Each multiplying a symmetric matrix.
 And then maybe adding another symmetric matrix at the end
 and saying that's negative semi-definite.
 You could say positive.
 You just have to make everything put minus signs in.
 But this is a conic constraint.
 Constraint.
 And it's one that's also known as a linear matrix inequality.
 So what I'm saying is
 for X to be a feasible thing,
 X1 times F1 plus all of this sum
 plus this matrix here has to have all of its eigenvalues
 less than or equal to zero in there.
 And you might put a linear constraint in there.
 But this is the sort of basic formulation
 of a linear matrix inequality.
 And it generalizes significantly.
 So we can write almost all of the other problems
 I've already given you in this taxonomy
 as linear matrix inequality constraints.
 Sometimes they're pretty trivial.
 These might just be diagonal elements and things like that.
 But you can write a lot of other things that way.
 But it lets us solve some problems,
 Well, if you're a control systems engineer,
 almost all of the theory you've learned
 in control systems can be written
 as a linear matrix inequality constraint in there.
 And so I'll give you some examples of that.
 Okay.
 The first thing is,
 suppose you've got multiple constraints in there.
 So you've got maybe,
 I don't know, what have I said,
 n constraints in here.
 And satisfying all n constraints
 is the same as satisfying this one single constraint
 where all I've done is I've put each one on the diagonal.
 Because, of course,
 the eigenvalues of things on the diagonal,
 the eigenvalues of this whole matrix here,
 the eigenvalues of this,
 union with the eigenvalues of this,
 all the way down.
 So having them all less than or equal to zero
 is just exactly the same thing.
 So what that means is we always just write down one of these things.
 In practice, if we've got multiple of them,
 then conceptually you can put them on a diagonal.
 But you wouldn't solve this as one big matrix problem
 because it's got so many zeros in it,
 you're actually better off splitting it up into pieces.
 And the software would split it up into pieces.
 So there's no real distinction between
 one constraint or multiple constraints.
 There's one really famous trick here
 that's used for all of these,
 a lot of these linear matrix inequalities.
 When you look at some equations or constraints,
 which look like they've got quadratic terms
 and stuff like this in them,
 and you think, no, no, that's not linear.
 Well, this trick makes a lot of things linear
 that were not to begin with.
 OK.
 It's called a Schur complement in this.
 You've probably seen it before.
 So if I have a matrix that starts here,
 symmetric matrix,
 so Q, S, and R forming this matrix,
 now Q and R have to be symmetric,
 but S doesn't because I've got S transpose over here.
 So it makes the whole thing symmetric in there.
 And if I want to say, is that positive definite?
 Well, that is positive definite.
 Let me put some constraints in here.
 So Q is positive definite.
 R is positive definite.
 Well, positive definite.
 You can see that writing this down there,
 that has to be true
 because I could multiply by 1, 0, 1, 0
 and just get Q,
 or 0, 1, 0, 1, and just get R.
 And those are examples where I need them to be positive.
 All right.
 So if that's positive,
 this is if and only if R is positive,
 as I've said,
 but Q minus S R inverse S transpose
 is also positive.
 Now that's,
 essentially when you look at this piece,
 OK, that's quadratic in S here.
 But having that quadratic in S
 where R inverse exists and is positive
 means I could form this matrix
 and this matrix is linear in S.
 So now I've got matrix,
 it's linear in all of these pieces,
 Q, R, and S,
 whereas this equation is not.
 You can see it's quadratic in S in here.
 So you can push it in this direction
 to take equations or constraints which are quadratic
 and turn them into linear constraints on a larger matrix.
 So what is this doing?
 So one,
 actually one way of thinking about this is
 suppose the simplest example I could imagine
 is I have just a scalar quadratic function.
 Right.
 So here's basically a quadratic function,
 something in X squared and X.
 And I want to ask the question,
 are there any values of X
 for which this is negative
 or is it always going to be positive?
 Now if I draw the graph,
 oh no, it's negative in this region,
 so I know it's not positive for all values of X.
 But if I just gave you the equations,
 the coefficients,
 AX squared plus BX plus C,
 and give you the ABC,
 could you tell me that?
 So if I gave you the ABC,
 then how would you figure it out?
 You'd turn on software and plot it
 and then have a look.
 But OK, quadratic,
 first you check,
 is the A positive?
 Because the A is negative
 going down that way
 and clearly it's going to minus infinity.
 So you check if A is positive.
 A is positive.
 And if that's true,
 you say OK,
 how do I check that it's not this case here?
 Here I've got A,
 does it dip below the line?
 How do you check that?
 This is optimization class.
 You know how to check.
 That's the minimum, right?
 You want to see is the minimum negative or not?
 Sorry?
 Not just C,
 you have to do a little bit more substituting.
 C alone doesn't give it to you
 because of the B term
 which might shift it from side to side.
 Basically C is that value there.
 That might be above
 and the minimum value is below.
 They've kind of given it away.
 There's the minimum value.
 Differentiate your quadratic,
 set it equal to zero,
 and you get the minimum,
 or you get the X
 which is the minimum value,
 substitute that back in
 and then see is that positive or negative?
 And if you do that step,
 that gives you this equation
 and this gives you the A greater than zero equation.
 So that's conceptually what's going on
 if you have a very, very simple thing.
 And saying that this is positive for all of them
 is essentially testing this.
 So that is the calculation of that point there.
 If you think about differentiating,
 setting it equal to zero,
 and then solving,
 substituting back in.
 Of course, you could have a matrix
 that looks like this
 and that would be positive everywhere.
 So this would be one
 where you can form a matrix here
 and it would be positive,
 this would be positive,
 this would be positive,
 so it would be positive for all values of X.
 So that's what the Shur complement does.
 It's a mathematical trick.
 It's a fairly simple thing to prove in there
 and you can use the argument I gave you
 just for a one variable example
 and carry it through for vectors
 and then you'll be able to figure it out.
 But it also holds for affine combinations.
 So if all of these entries in here are functions of X,
 then this is also true
 because you might be looking for
 what's the value of X that makes this happen.
 Maybe this represents some beneficial thing
 you want your system to have
 and I'll give you an example later.
 Then you might look for the value of X
 that makes this true.
 So if you have a value of X
 that makes all of this true,
 the easiest way to write it
 is to form the matrix
 and look for the value of X
 that makes this true
 and this is now linear in X.
 This is definitely not linear in X.
 You can see X appearing here in a quadratic form
 and it's on a denominator as well.
 So it's a long, long way from being linear in X.
 This is linear in X
 and so we've told that.
 So what we're going to do
 is we're going to turn our interesting objectives
 in our control design
 which when we write them out look like this,
 we turn them into this.
 And doing that's a little bit of an art
 and you'll see in there
 and it's still true that if you find a nice way
 of writing down some objective,
 control objective
 and you turn it into a linear matrix inequality
 and nobody else has done it before,
 you can get a nice publication
 and maybe even a PhD out of that.
 So we haven't exhausted all options for this,
 I would say.
 Okay, I'll give you some examples
 and I'll give you a real control example.
 Just matrix problems.
 So here we want to minimise a matrix A of X
 and so this A is a linear function of X.
 And we want to pick a value of X
 which makes this small.
 Now the 2-norm of a matrix
 is the maximum singular value
 or it's called the spectral norm.
 Maximum singular value.
 A mathematician might say spectral norm.
 It's a function, we might want it to be small.
 If you're in any dynamical systems,
 knowing the 2-norm of this
 is essentially the maximum singular value
 if you think of a matrix is the maximum gain.
 If you put in a unit vector
 and you multiply it by a matrix A,
 what's the biggest A times X that you can get
 and how large is that?
 And the size of it is the maximum singular value.
 So you might want to make that small.
 So if you think of a matrix
 which represents the gain
 from your noise in the system
 to the errors in your control action in that
 or you might say,
 if I gave you an example of an autonomous driving example,
 it might represent the wind force on your vehicle
 versus the output to the steering error
 that you have in your autonomous steering in there.
 And you obviously want your control system
 to make that as small as possible.
 You want to make the minimum error in steering.
 Or more particularly,
 if you built the autonomous car
 and I'm on the other side of the road,
 I want to make sure that your autonomous car
 is minimizing the error there.
 So that's a motivation.
 There are many, many motivations.
 But the way the trick works here,
 so this, again, you put a constraint
 which is an epigraph.
 You say it's less than some gamma.
 So that's equivalent to basically saying
 gamma squared minus a squared is still positive.
 That means a is less than gamma.
 Okay?
 But for matrices, you have to use the square there.
 And so to put that as an equivalent form,
 this is minimize gamma subject to this.
 This constraint is an LMI constraint
 because you see it's actually linear in x
 and linear in gamma.
 The way you get it is you start with that condition.
 Here's the squared term.
 And then you perform the sure complement operation.
 And here's the matrix you get.
 I mean, this one actually you do something a little...
 You also say because gamma is positive,
 I can write it like this.
 One over gamma.
 You can divide by gamma, right?
 That still has to be positive.
 And now you do sure complement on that
 and you apply the definition.
 So that would be gamma i minus a 1 over gamma a transpose.
 You apply the definition there
 and then you form that matrix.
 And it's exactly that.
 So that's an example of using the sure complement
 to minimize the maximum singular value.
 And this is linear in both the gamma and in the x's.
 So when you minimize,
 you actually find the smallest maximum singular value.
 That's gamma.
 And you find the x that achieves it.
 Okay.
 So some other things.
 Ellipsoids.
 You want to check whether an x is in an ellipsoid.
 So remember we had...
 Was it yesterday or even earlier?
 Maybe it was just yesterday.
 We had an ellipsoid.
 So here's a formula for an ellipsoid.
 x minus the center of the ellipsoid
 basically squared with a weighting of p less than or equal to 1.
 Now apply that.
 Subtract the 1, take it to the other side.
 It's less than or equal to 0.
 Apply the sure complement
 and you can see x being in the ellipsoid
 is equivalent to this lmi.
 Or I could swap it around.
 That's less than or equal to 0.
 I could write it around by negating this.
 1p xx minus c.
 So testing whether or not some x is inside an ellipsoid
 is just a linear matrix inequality.
 Now you can start...
 If you're given an x or you're given a whole bunch of x's
 you can start optimizing over this
 because this is linear in almost everything you might care about.
 It's linear in the x's but it's also linear in the centers.
 It's linear in the scaling p.
 So you can optimize over all of those
 or any of those variables.
 If I gave you 5 different x's and said
 find an ellipse that goes around them
 then this would have to be satisfied for a center and a p
 such that putting all 5 ellipses in there
 gives me a positive semi-definite constraint.
 So it is actually used that way
 but that's a very simple test.
 Whereas when you look at this
 it's not quite so simple.
 There's an inverse in here.
 You can see x appears here and here.
 It's squared but the Shur complement
 turns it into a linear matrix problem.
 Okay, so CDX.
 I'll give you a very brief introduction to this.
 This is available in Python and also in MATLAB.
 And if you pay money you can get it as embedded code
 to put in...
 Actually, it's used extensively.
 I think it's used in SpaceX for landing
 the rocket boosters back on Earth.
 It's used in autonomous driving stacks
 and it's very, very good software.
 The basic ideas behind it have been used
 also for navigating planetary landings.
 Not this planet, other planets.
 In particular asteroids, approaching asteroids.
 So this approach has used variations of CDX
 or things like that in order to solve these problems.
 So here's just a simple example to show you
 how it's easier to code.
 Let's say I have got two ellipses
 and I want to find the minimum distance between them.
 There's ellipse one, there's ellipse two.
 Okay, the minimum distance is zero
 because anything in that intersection is in both.
 But maybe there's another ellipse three out here
 and I want to know the minimum distance between
 this ellipse and say this ellipse.
 Then that involves finding a point in this ellipse
 and finding one here
 so that the distance between them is minimized.
 So I'll call this one x1, this one x2
 and then I want to minimize the two norm of the distance.
 Notice I haven't squared it.
 I'm keeping it in conic form.
 Subject to x1 being ellipse one, x2 an ellipse two
 and that's exactly the LMIs we'd write down.
 So you minimize this function
 and here are the two LMIs.
 The first one says, okay, x1 is in ellipse one
 if it satisfies that.
 So the shape of the ellipse is given by P1.
 The center is given by xc1.
 Same for ellipse two.
 And this is the code that solves the problem in there.
 You just define your two variables
 that you're optimizing over, x1 and x2.
 You've got to find those.
 Your cost function is the norm between the two.
 If you don't say otherwise, it assumes the two norm in there.
 I've written here subject to.
 This code, whenever it sees subject to, it just ignores it.
 It's only put in there to make the code easier to read.
 And these are the constraints expressed in MATLAB notation
 which I think is probably very similar to Python notation in that.
 And you can see they're almost exactly essentially those.
 Here's that matrix.
 The semicolon in MATLAB means go to the next line of the matrix.
 So I've just written these matrices
 and the variables x1 and x2 appear in the matrices.
 The P1, P2, xc1, xc2,
 those are the data that define exactly where your ellipses are.
 So that's an example of code.
 And you can get it in a stack
 which allows you to actually write it that way
 and turn it into embedded code in there.
 So it's very, very handy for using and also for checking out.
 But it won't do every convex problem.
 It's what's called disciplined convex problem.
 I don't know who's disciplined in it,
 but essentially it will only do problems that you can prove to be convex.
 In other words, things like monotonic functions of convex functions or affine functions.
 So it has essentially grammatical rules for checking whether or not
 what you've written down here is convex.
 And there are convex problems which you can't write in its little grammar.
 It's slightly restricted.
 But it covers a huge amount.
 Okay.
 So in LMIs,
 so they are quite general.
 So, for example,
 all of my previous things I can turn into LMIs.
 So a linear constraint, ax less than or equal to b,
 as a matrix constraint,
 essentially it's just putting the linear constraints on the diagonal.
 Sort of a trivial one.
 If I have a quadratic constraint,
 and it's convex,
 so this is strictly positive q,
 then it's equivalent to that LMI.
 You can prove that with the Shor complement.
 It's a very, very simple application of the definition.
 If I have a second order cone constraint here,
 here's my ice cream cone,
 it's equivalent to that LMI.
 So all of these previous ones you can just write
 as linear matrix inequality constraints.
 So that's why we focus on linear matrix inequality constraints,
 because everything else sort of trivially fits into that.
 When you use CDX,
 you can write them,
 here I've written them as LMIs,
 but actually I think for some of these things
 you can actually write them directly in some of these forms.
 Oh, there's one important thing about this.
 I should point out if you try and do it.
 There's this SDP,
 semi-definite program,
 flag that you put in there,
 that says interpret matrix constraints
 in the positive semi-definite cone,
 not as element by element.
 MATLAB defaults to element by element.
 If you put SDP there,
 it means, oh, I want a positive definite matrix.
 Okay, so I'll finish up
 at great speed
 using an example which some of you have seen,
 and I overheard someone talking about this last week,
 so I thought I'd do this as an example.
 And it's linear quadratic regulator,
 which I think you've probably heard a little bit about.
 Okay.
 Excellent, excellent.
 Okay, so you already know the answer.
 I'll show you how to find it,
 or another way of finding it.
 So you know the Lyapunov conditions
 for stability of a system.
 So here's a continuous time system.
 I haven't put an input on this one yet.
 I'll add an input later.
 So just think of it as autonomous.
 And you've got the derivative is A times the state,
 the derivative of the state.
 Now, that's stable if and only if
 there's a positive semi-definite matrix
 that satisfies that.
 You could write that as an equals or less than or equals,
 and then you're solving what's called a Lyapunov equation.
 All right?
 But you can write it as an LMI.
 Anything satisfying that will satisfy.
 And that's a linear matrix inequality.
 So checking that your system is stable
 is a linear matrix inequality.
 It's also true in discrete time.
 You have to work just a little bit harder.
 So here's the discrete time,
 the state at time k plus 1
 is A times the state of k.
 And that's stable if and only if
 there's, again, a positive definite matrix
 such now it's A transpose P minus P is negative definite.
 But it's proven exactly the same way.
 I haven't got time to go through the proof,
 but you probably did that in your linear systems
 how you prove that.
 This is just proven the same way in discrete time.
 But that's also an LMI.
 Let me just put that on there.
 This is also an LMI.
 It's an LMI in P, I should say.
 In P, not in A.
 You see there's an A squared there,
 but how do you get rid of that?
 That has exactly the form of the Schur complement.
 So you perform the Schur complement and you get this.
 Now, when you look at that,
 you just think, ah, that might be an LMI in P,
 but then you go, oh, wait, there's a P inverse here.
 That's not linear for sure.
 But if you multiply by one side or the other
 by identity 0, 0, P,
 identity 0, 0, P,
 it's basically multiply both sides.
 It's called a congruence transformation.
 But it's essentially, it's not going to change
 the sign definiteness of this.
 It's like adding a squared piece on each side.
 The first P cancels that one,
 and then this P then makes a P,
 and you get this.
 So this LMI is linear
 in P and A.
 One or the other.
 Maybe I should say P or A.
 If I'm looking for A and I have a P,
 I can solve it as an LMI.
 Or if I have an A and I'm looking for P,
 I can solve it as an LMI.
 So now I'm going to focus on the discrete time
 because that fits in more with the way we typically do this,
 particularly in model predictive control.
 Okay, now I've got an LMI.
 It's not quite the one I want,
 and we'll see in a second.
 And so now what I'm going to do
 is discrete time state feedback,
 which is this linear quadratic regulator.
 So now I've got an input,
 B times U going into the state.
 I've got my A matrix,
 and I'm looking for state feedback gain,
 U equals A plus BK.
 So if I put in U equals KX and I substitute this in,
 you see these are my closed-loop dynamics,
 A plus BK.
 And the game is to find the K, right?
 That's your control design here.
 Now, you want this to be stable, for sure.
 And so that's stable.
 I'll apply that LMI to it.
 It's stable if and only if I have this.
 Now you can see instead of A, I've put in A plus BK.
 So I'm interested in when I turn the feedback on,
 am I stable here?
 Another way of doing that is to,
 I write it this particular way,
 and actually you can see if I make Y equals P inverse,
 it's invertible,
 and again I put in a multiplication by P inverse
 on both sides,
 then I can turn this into this.
 These are exactly the same.
 I have to make the substitution
 and then do the congruence transformation I showed you before,
 but I'll get it this way.
 Well, why I want it this way is that y and k appear to multiply each other in here.
 And this is going to get rid of the trick here.
 When I look at P here, I end up with a product of unknowns.
 P is unknown and k is unknown.
 But now the way to solve that is to make a substitution, ky equals v.
 And now write the LMI.
 And so when I multiply A y, I keep that A y.
 But now ky equals v, I get B v.
 And now consider my optimization variables to be P, or sorry, I should say y and v.
 And so I solve this.
 As long as I can find y and v, I've found a state feedback.
 Well, I haven't quite found a state feedback yet.
 I've made this definition, so once I find y and v, I've got to say k equals v y inverse.
 And now I've got the k.
 And that k comes with this y, which is the Lyapunov function.
 It says this is a stable system in there.
 And so that's how you design state feedback.
 This is the feasibility condition in there.
 You want to have an objective.
 So I'm going to give you a cost function.
 So here, let's say we have a system which, here's our system,
 but we've got some sort of either a disturbance or an input which
 fits an initial condition.
 Either way, you want to think about it.
 State feedback, and this is our closed loop here.
 Now my cost function, is this the one you've seen before?
 That's the one we would like to minimize.
 And I can write it in terms of x, because I've got u equals kx.
 I've just written this in terms of x.
 Make this substitution in for u, and then split it up into square roots.
 And I get it in this form.
 But this is what I'm trying to minimize.
 And my final step is to give you a theorem which says that cost function is less than gamma,
 if and only if I can find a matrix W and P such that these three conditions are satisfied.
 The trace, or some of the diagonalments, is less than gamma.
 This is a positive definite, and then you can see this is an LMI in here almost,
 except I've got P times k.
 And so I do the same trick with the P times k.
 Well, I've got these three conditions now, three constraints to satisfy in here.
 And then I'm guaranteed that that cost function is satisfied.
 So here's my design optimization.
 Basically, minimize gamma subject to that trace constraint.
 Now I've made the substitution v equals kp.
 So now I've got an LMI in here.
 This is also an LMI.
 And these are the variables I minimize over.
 W and P are positive definite, but v doesn't have to be.
 And then I get k.
 So that gives me the optimal linear quadratic regulator.
 That's an LMI problem.
 And you could more or less write that as CVX code exactly as I have there,
 and you would get a solution.
 You can put trace into CVX and write it like that.
 What else can we do?
 This is just very quick.
 We're not going to do any of that.
 That was more or less the simplest control design problem.
 And you're probably thinking, that was kind of difficult enough.
 It can get much more difficult.
 But you can use all of these methods for things like pole placement
 in regions for closed-loop systems.
 You can minimize the gain of a system, the h infinity gain,
 which is maximizing the value, or the 2 gain, which is minimum variance.
 You can design carbon filters in this.
 If you don't know what a carbon filter is, don't worry.
 It's your best estimate of the state from measurements.
 You can also look at analyzing stability and performance.
 If you vary A and B a little bit, are you still stable?
 That's an LMI condition.
 And you can design for variation in A and B.
 I'm allowed a 10% variation in all the elements of A and B.
 Am I still going to be stable?
 That's another LMI, a much more complicated one.
 But it's got about five by five big block matrices.
 But you can do all of those things as well, which is why we really
 like these things in there.
 But I think that was the simplest example of a design problem with LMIs.
 So sorry for accelerating here at the end.
 Are there any questions?
 Yeah.
 This is something that's similar to something I've been running into,
 called a Joukowsky re-parameterization.