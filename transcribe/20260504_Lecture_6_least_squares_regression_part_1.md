 My great pleasure to welcome Professor Roy Smith from ETH Zurich. He's come all the way
 here to teach you, so I think it's a great privilege and we're all looking forward very
 much to learning from your lectures. I think I also posted to the course page about the
 workshop which you're also welcome to attend. 10 undergraduates are part of the scope, so
 I think that's about it. I'll hand it over to Professor Roy. Thank you very much.
 Thanks very much Jeremy and thanks for hosting me. So I'm coming for a month as part of the
 Visiting Estonian Fellow, which you probably may or may not know about, but I'll be teaching
 and around for this month. You can probably tell from my accent that I'm not really Swiss
 and actually I got my undergraduate education right here in the late 1970s. Things have changed
 a little bit, but you know those lecture halls on the other side of the lower level? That's where
 I was educated in E6 and E7. So I've been through in exactly the same position you are, so you might
 be curious about how am I end up in Zurich. I was 20 years a professor in the United States,
 UC Santa Barbara as well, and I've worked in industry and I've worked for NASA in a variety
 of projects. So if you want any advice on career or options or things like this, apart from a lot
 of good luck, how did that work out? Then please feel free to send me an email. I'm happy to chat
 and give you advice on that. So you're starting right at the same trajectory point that I was in,
 so you can see how it might end up one way for better or for worse. Anyway, actually I officially
 retired last year from ETH Zurich because they have a mandatory retirement age, but I can't quite
 give it up, so this is part of the reason I'm back here. And I'm going to teach you a bit about some
 optimisation topics. I've put together some slides from a variety of courses that I have taught in
 the past. So my usual style is to really encourage some interaction. If you've got any questions at
 all, just feel free to interrupt me. Swiss tend to be a little more polite. I've also taught in
 Ghana and Africa these topics as well, and they're much more excited and energetic down there because
 to have a professor come from Switzerland is not all that common, and they realise that your time
 is valuable, that you'll be gone in a couple of weeks, and so they ask everything they can possibly
 think of in the class, and so we spend the whole day. So somewhere between those two would be pretty
 good. So anyway, let me start. And so I wanted to start here, because we have 50 minutes I guess,
 talking about least squares regression, which is quite a basic thing, but I thought I would
 introduce it because it's also a very good way of highlighting some aspects of optimisation,
 which appear not to be first to be least squares, but least squares or the ideas behind are buried
 inside. And also on the other side, you can take some of the ideas you do see in big optimisation,
 large-scale optimisation problems, and then look at them and realise that they're much easier to
 understand in terms of least squares problems, where the basic things are linear, and so you can
 see what these things are doing for you. So least squares I'll probably talk about in the next two days,
 plus or minus depending on how far we get. So anyway, let's begin. So I wanted to talk about what was
 the hot science topic of 1800. So we're going back to the beginning here. And that was to try and find
 an undiscovered planet in there. And about that time, well before 1800, this was the current list of
 planets. I've left Earth off. But it was in there, and they were aware of that. So science at the time had
 discovered everything out to Uranus basically, and actually I think this was 1778, so this was not much
 more recently. And there, why a missing planet? Well there's something called the Titus-Bode Law,
 which is this formula, d is the distance from the Sun to the planet, in normalised units. It follows this
 sequence. So d is 0.4 plus 0.3 times 2 to the n, and n is minus infinity, 0, etc. in there. And that does give you a
 pretty good approximation, at least for a circular approximation to the orbits, the distance of all
 Now, Earth is 1. If you put n equals 1 there, you get Earth in there. Venus is 0, and Mercury is minus infinity.
 But they made up this nice little sequence, and one very disturbing thing about this sequence is there's no
 number 3 in it. And so, how come there's no number 3? There must be a planet we haven't discovered in there.
 And they had a pretty good idea of the distance, but it doesn't tell you exactly where it is in the sky.
 You guessed it might be in the ecliptic plane, but you wanted to find it. So the hot topic of 1800 was,
 well, let's try and find this planet. There isn't a planet at 3. That's roughly where the asteroid belt is.
 There might once have been a planet at 3, but it's been broken into pieces. And so the largest thing
 there is Ceres, which is only a bit under, or just a bit over 900 kilometres in diameter, so it's pretty small.
 But it's enough to see. It was very hard to see with telescope technology of 1800, but it was definitely the problem
 to try and find that. So, that problem, I have a little history here. So in 1801, Giuseppe Piazzi, he did find Ceres,
 actually, and he made 22 observations of it. So he got his telescope out, and an observation consists of two angles,
 basically. So if you sort of head to the vernal equinox out at one side, you've got a sort of what's called a right
 ascension angle to the planet, and then there's an elevation angle up, and then you see where the planet is.
 You record those. So each observation is two numbers, two angles, basically, and he made 22 of them over what
 took him 44 days. Weather wasn't always great, he was in Italy, and he saw basically 22 observations, 22 measurement points,
 each one is two numbers. Now, in February, Ceres, trapped behind the sun, because Ceres is going round one way,
 and the Earth is going round another, or in the same direction, it wasn't going to be visible for quite some months afterwards.
 Now, it was so hard to find, they wanted to predict when would it come out from behind the sun, so they could be sure to see it.
 So the observations he had corresponded to about 9 degrees of arc, so that's not very much to make a prediction.
 So this was published by a scientist in an astronomical magazine called ZACH. He published the observational data,
 and all of the astronomers of the day tried to estimate when Ceres would appear on the other side of the sun,
 and where exactly they should look for it. So Gauss, pictured here, he estimated the orbit of Ceres,
 and ZACH published the ephemeris, which is essentially the parameters that characterize the orbit there,
 along with those of many of the other hot astronomers of the day.
 But Gauss was significantly different to most of the other astronomers.
 Then, on 7th of December, so you see this is 10 months later, ZACH himself got the telescope out,
 and found Ceres within half a degree of where ZACH said it would be, but Gauss would not say how he'd done the calculation.
 So he was accused of sorcery, and it's a great way of destroying the reputation of your academic opponents.
 Anyway, he found it. The same thing repeated in 1802, Pallas, which I think is the second largest of the asteroids,
 was estimated a few points off, measured, and Gauss estimated that orbit, and then he still wouldn't say.
 In 1805, Le Gendre published a paper on the method of least squares,
 but was aware that this is probably what Gauss was using, even though he wasn't saying it.
 And Gauss had actually been using it even five years earlier for making predictions of the trajectories of comets.
 So he'd worked on some of these techniques.
 So on the basis of being able to do that, he became director of Gershwin Observatory.
 Another astronomer discovered Vesta, which is the third largest of the asteroids,
 and Gauss took only 10 hours to calculate its orbit.
 Now, 10 hours to calculate the orbit from a number of points, no calculator, no computer.
 It was basically actually quill and ink on a piece of paper.
 And you can read his notebooks. I've had a look at some of his notebooks.
 You can look at them online.
 And there's quite a few pages, and he very rarely made any mistakes.
 So, I mean, I don't think I could code up the software to do that in 10 hours,
 let alone actually run through every calculation.
 And he did his calculations to about eight decimal places by hand.
 So incredibly impressive.
 Actually, I should go back here.
 When I'm thinking about Gauss, he came from a sort of lower middle class background.
 His father worked for a landowner, I think it was,
 and it was quite a generous person who offered to fund Gauss to go to a school.
 And it was in school once, and the teacher was a bit bored,
 and he wanted to give the class something to occupy them for a certain period of time.
 So he asked him to sum up the numbers from 1 to 100.
 And Gauss took about two seconds to do that.
 How did he do it?
 He didn't start at 1 plus 2 is 3 plus 3.
 He did not do that.
 So he said, OK, round about 50, 49 plus 51 is 100.
 48 plus 52 is 100.
 So you've got 49 times 100 plus the 50 plus the 100.
 Done.
 And the teacher saw how he'd done this and thought,
 this kid, he was quite young, is special.
 So he paid for the education higher and higher for him.
 So anyway, he got to become the director of Göttingen Observatory.
 And it was 1809 that he finally published the paper
 that outlined the methods of these squares in there.
 So actually, I offered to give you some career advice.
 Don't do this.
 Don't come up with the best methods the planet has seen for hundreds of years
 and then take 10 years to publish it.
 If you've done something pretty good,
 you should probably publish it fairly quickly.
 So anyway, what did Gauss do?
 All right.
 And I'm going to start with a simple example
 and we'll work up to what he actually did today.
 And that's fitting data to alignment.
 This is something I remember seeing in high school,
 probably seen a similar thing.
 And that's certainly in your first year.
 You've got a series of points on xy plane.
 And I've got them, you know, x1, y1 up to xn, yn.
 So I've got these and I would like to have a line go through all of these points.
 So this is ax plus b.
 So the things I need to figure out are what's a and what's b.
 These are the sort of unknown parameters in this.
 Now, ideally, you've got a case, well, there's this relationship which holds.
 And I would call that roughly, I would call that sort of a model of what you expect.
 In reality, particularly if these are measurements of things,
 this never really happens, but you've got some errors in there.
 And typically, for here, we can assume the errors are in y.
 So we know the x's, but y could have some errors in them.
 So the real model of our system, including the errors,
 would add, say, an epsilon i to each one of those in there.
 And so we have a matrix equation.
 Vector of the y's, a's and b's.
 And if you look at each row of this, this is y1 is x1 times a plus b plus epsilon 1.
 It's exactly that equation.
 So all of the rows are just written down in matrix form in there.
 And I've given some symbols for them.
 Y is pretty obvious.
 This one here, this matrix, I'll call phi.
 And it actually has another name in what we're going to do.
 It's called the regressor matrix.
 So that's phi theta.
 I'm going to use as a variable, which is my unknown parameters.
 So theta, unknown parameters.
 And my job is to find those parameters.
 And epsilon is just going to be a vector of errors or noises, if you like.
 So that's linearly squares.
 It's to essentially solve the problem of finding the a and b that satisfy this.
 Now, if you have a look at how many unknowns you've got here,
 you've actually, obviously, a and b is two unknowns.
 But if you've got all of these epsilons, there's another n of those.
 So you've got n plus 2, and you've got n equations.
 N simultaneous equations, if you like.
 So clearly, this is not unique.
 There are many infinite number of choices that will satisfy this.
 So you're looking for what is, quote, the best one.
 And the best one, we're going to say, is the one with the smallest noise in here.
 There's a couple of good reasons why we're going for smallest in there.
 And we'll get to these, I hope, by the end of today.
 So we look for the smallest one.
 And we typically, as you might expect, actually look for the smallest
 in terms of the square of the entries here, the sum of the square,
 or the 2-norm of the entries of the epsilon.
 That's going to be our idea of the best possible fit in that,
 which is where the name comes from, least squares, as you might expect.
 It's very honest about that.
 OK.
 So here's our linear fitting.
 We have a model equation.
 This is why I call it a model.
 In the previous example, this was the fact that a line goes through these points.
 So it may or may not be true, but that's what we assume.
 And that's why I say it's our model of what's going to happen.
 In general, let's say we've got n points.
 And let's say we've got d parameters to get.
 d was 2 in the previous example.
 So that's a d-dimensional vector of theta.
 And the regressor matrix is, of course, n by d.
 Now, if n is bigger than d, so you've got many, many more rows,
 then you have an over-determined case,
 in the sense that this equation alone
 is going to have many, many ways of coming up with the theta,
 if it's exact.
 Now, of course, in practice, it's never exact.
 It's quite possible that n would be smaller than the number of parameters.
 Now, actually, it's becoming increasingly possible these days.
 So this is the case we normally think of it.
 You have a lot of measurements.
 You're trying to fit a line through it or maybe a parabola or a circle,
 but you have some simple form.
 You're a relatively small number of parameters,
 and you're trying to find...
 We've got lots of measurements of this.
 This case, though, comes up frequently in machine learning.
 And that's the case where you've got models
 which have many more parameters than available data.
 And that's become a very common thing in this.
 And so there, it's under-determined.
 There are actually an infinite number of thetas which will do the job.
 A lot of big question with machine learning,
 what's the meaning of the fact that there's an infinite number of them,
 and how do you handle that?
 So we'll get to that,
 but the under-determined case comes up more often than you might expect,
 particularly in large-scale data cases or large-scale models.
 And if you think about large language models or vector support machines
 or essentially any of these machine learning methods,
 often they have a huge number of parameters,
 millions of parameters in language models,
 and not so many data measurements.
 OK, but a lot of what I'll focus on here,
 and in a lot of engineering applications, this is the case,
 that it's over-determined.
 You do get more measurements than the parameters that you're looking for.
 So, because this is an engineering class,
 I want to put this in an engineering or non-engineering optimization context.
 One way of sorting this out is to, say, introduce these errors epsilon.
 Think of the objective to be minimized as the square,
 the two-norm squared, if you like,
 the sum of the squares of the elements in there.
 It doesn't matter so much that it's squared.
 It makes the mathematics easier,
 particularly when you come to differentiate it,
 in that you get the same answer, but we typically write it as squared.
 And subject to this constraint,
 so your measurements y are explained by phi times theta plus some noise,
 and you're trying to make that noise or error as small as possible.
 This is also known as an equation error form,
 because essentially you would like that epsilon to be zero.
 That's the constraint you would like to satisfy.
 It's generally not possible for, just picking arbitrary y,
 this will not be a consistent equation equal to zero in general.
 So we call it an equation error,
 and this will come up a little bit later,
 is sometimes the equation error corresponds to the physical intuition
 we have about the system.
 So if y was really subject to measurements,
 x are all in here, measurement errors,
 and x all in here are not,
 then this is also a reasonable model of measurement noise.
 And so you think, okay, small measurement noise,
 what's the smallest measurement noise that describes my model structure?
 And making it small is likely because for measurement noise,
 we typically assume that, I'll draw the shape,
 it has some probability density function like this,
 and it's zero mean, typically.
 And so get it as small as possible means it's the most likely thing
 to have explained the result,
 because it's close to the middle here.
 And the middle is where the density function is highest.
 So that's motivation for making it small
 in terms of the probability density function.
 Now, if that's your entire problem description,
 the easiest thing to do is to take that epsilon,
 substitute it in here,
 and you end up with this optimization problem.
 And this one's unconstrained.
 And it makes it a little bit easier to solve.
 You don't have to work out KKT conditions and things like this,
 which I think you probably suffered with last week or so.
 You just, how would you solve this?
 You just differentiate it, set it equal to zero.
 That would be the obvious way to do that.
 So it's a little bit easier.
 You might not be able to do that
 because you may have some additional constraints that come up.
 You might want to constrain the theta to be in some other set.
 Maybe they have to be positive.
 Maybe there's some other convex constraint that you might want to add,
 in which case you can't quite simplify it like that.
 All right.
 So we'll look at this particular problem.
 Let's make the problem a little bit harder.
 We'll go through a couple of steps.
 And now, instead of fitting a line,
 I'm going to fit a linear function parameterization.
 Now, what I mean here is that I've got my y equals fx,
 but fx is not here, ax plus b.
 It's a little more general.
 It's a linear combination of functions hi of x.
 So, and each one is multiplied by theta i.
 So the hi, you can think of them as basis functions.
 They tell me the basis I'm looking for.
 When I go back to the simple example,
 this one, the basis functions are really just x and 1.
 Very, very simple.
 But there could be more general things.
 A common one might be polynomials.
 And I've given an example here where
 the easiest way of thinking about it
 is my polynomials are powers of x.
 So if I'm after a second order, a quadratic function
 to fit through my data points, I would choose 1xx squared
 and then find the values of theta, which
 would multiply each of these to give me
 a general third order or second order polynomial.
 This certainly works in definition.
 It's not perhaps the best thing to do.
 A better one is to use Chebyshev functions.
 So again, the first one's 1x, and then this one's
 2x squared minus 1.
 And you keep going up.
 You can calculate what the next one is.
 It's 2x times the previous one minus the one before that.
 And I've plotted both of these options over here.
 And you see the red dashed lines are the regular polynomials.
 I think I can see 0, 1, 2, 3, 4.
 So basically, that's the fourth order polynomial shown there.
 And here, I'm showing it also for the Chebyshev functions.
 And you see quite nicely that they look much more
 interesting, if you like, through most of this graph.
 So they have different functions that
 can fill everything in the graph.
 If you look at 0 and you think of the powers there,
 the only thing that can fit data near 0
 is the constant line there, when x is close to 0.
 Whereas in the Chebyshev, you've got multiple options.
 You've got this one.
 You've got this one, and higher order ones.
 So the number of points or the fit
 that you can get across a minus 1 to 1 normalized interval
 is much better with the Chebyshev functions.
 What this comes out to mean when you apply it
 is that the matrix phi is better conditioned than this.
 Whereas this one might be poorly conditioned,
 depending exactly on where the x's are.
 There's lots of ways of explaining data here or data
 here in this, but not much as you get down here.
 So it could be you're fitting much more complicated functions
 than just lines, but the key point
 is that you're still fitting a linear combination
 of these functions.
 So you still have a linear combination
 to look for when you do that.
 So we could do this.
 This wouldn't be particularly good for finding
 the orbit of a planet, or a comet,
 because these describe polynomials.
 Comets and planets don't travel along polynomial functions.
 They actually travel along conic sections.
 So we can do something similar for those.
 OK, well let's first talk about least squares.
 So here, let's say the simplest problem,
 I've given you a couple of examples
 of what you might use for that, is to find the closest fit.
 So this would be the smallest epsilon in here.
 And I put it in the simplest form.
 It's an unconstrained optimization problem,
 and it has this cost function.
 So let me just write the cost function down, say, J.
 It's a function of theta, which is
 the variable I'm looking for.
 And you can see it's equal to phi theta minus y transpose phi
 theta minus y.
 So that's the sum of the squares of the elements of that.
 Think of a row vector and a column vector.
 So you just get the sum of the squares of the elements.
 And of course, that's actually equal to 2 norm v squared
 in there.
 All right, so one way of doing it is to multiply this all out.
 We can do this.
 This would be theta transpose phi transpose phi theta minus 2
 phi theta transpose y plus y transpose y.
 y transpose y is not going to matter to us.
 But the two terms we have in here,
 we have a quadratic in theta here and a linear term in theta
 buried in there.
 So how do we solve this?
 Well, this is just a function of theta.
 Theta might be vector-valued.
 You can think of theta 1, theta 2, and theta 3,
 if you like, the components in there.
 We differentiate it and set it equal to 0.
 So differentiating that, I don't know how much experience
 you've had differentiating matrix or vector equations.
 Yeah, some?

 No problem.
 It wasn't really the priority of the idea.
 It wasn't the priority.
 Actually, it doesn't have to be the priority.
 It's the sort of thing that it's really nice to do once
 and convince yourself that it all works out
 in terms of where the transposes go and stuff like that
 and never do it again.
 Instead, go to this website, matrixcalculus.org,
 and it gives you boxes.
 You enter in your complicated matrix equation,
 and it finds the root in there.
 It's really great.
 Do it once just to make sure, because there are actually
 a couple of different choices of notation you can use,
 depending on when you're differentiating, say, a matrix.
 Do you go down the columns or across the rows first?
 So there are a couple of different ways of doing it,
 but there's some more common standards
 that you can find out a little bit more there.
 I'd say, once you've done it once,
 convince yourself that what I'm writing here is correct.
 Then you can go ahead and just use that.
 So we differentiate this, of course.
 There's a quadratic term there, so you'll expect to see.
 Whoops, OK, I've changed color.
 Too bad.
 2 phi transpose phi is the term for the quadratic times
 theta minus 2 phi transpose y.
 And we set it equal to 0 to find the minimum
 of this convex function in there.
 Phi transpose phi, of course, the quadratic term in here,
 there's going to be a positive definite matrix.
 Maybe only positive semi-definite in there
 if the phi is not full column rank.
 But we'll talk about that case a bit later on.
 That's what happens in machine learning.
 It's not positive definite.
 And so let me just shuffle this around a little bit
 and write down, let's choose a different color here.
 So we can write it down as phi transpose phi,
 put that in parentheses, theta equals phi transpose y.
 So you see, that's the linear equation
 that describes the solution here.
 And there's a couple of interesting things about that.
 Well, one is, we like it so much it's got its own name.
 These are called the normal equations.
 I don't know what the un-normal or sub-normal ones are,
 but those are the normal ones in there.
 So phi transpose phi times theta equals phi transpose y.
 And so the solution, the minimizers of this objective
 satisfy that equation.
 Now, this equation, y minus phi theta, is not always consistent.
 What I mean is, for any possible y,
 there doesn't always exist a possible theta
 that fits that exactly.
 But this is always consistent, which is an important property.
 It always has a solution for any y, any solution.
 And so we would call this consistent.
 Have to be a little bit careful here,
 because consistent has a different meaning as well.
 But the one we're looking for here is, you give me any y,
 and there will be a corresponding theta.
 Now, in the case where you've got an over-determined thing,
 what you can always do, of course,
 is this is a square matrix here.
 It's positive definite, so it has an inverse.
 So you could write your optimal theta,
 and let's call it theta star, is equal to phi transpose phi
 inverse phi transpose y.
 And that's the solution.
 You have a closed-form matrix form solution
 for your linear least squares.
 And you could code this up in MATLAB, do it exactly like that.
 I wouldn't in the sense that, theoretically, it's
 the solution.
 It's good for proving theorems.
 It's good for teaching a class.
 It's not always good for calculating.
 And the reason is, you've basically squared things here.
 So small numbers will get smaller.
 Big numbers will get bigger.
 Then you've inverted them.
 Those small numbers might get very big.
 And then you multiply them out again.
 So numerically, you can end up with problems in here.
 And in fact, if you're in the machine learning case,
 if you like, if you're in the under-determined case,
 this isn't really invertible.
 We'll talk about that tomorrow, about what
 you can do about that case.
 But this is the theoretical solution.
 And with a relatively small number of things,
 you could even code that up in MATLAB.
 It would be fine in there, unless you've
 got particularly poor data.
 But that's the solution to least squares problem.
 So yeah, that was quick.
 But I'll talk to you about a few more things about this.
 So I pointed out the normal equations are always consistent.
 And the point I want to make here is,
 you have to ask yourself, does phi transpose?
 Phi inverse exists.
 So if it doesn't, so if phi has, I'll call it low column rank.
 What I mean is, it's not the full column rank.
 So think of that matrix phi.
 You've got a tall matrix, if you like.
 It could be that some columns are a linear combination
 of the others.
 And then we say, that loses rank.
 So how many linear independent columns are in there?
 And if you've got d linearly independent columns in there,
 that's all of them, then this will always exist.
 But if it's low column rank, then actually you've
 got an infinite number of solutions, theta.
 Now, they all achieve the same cost.
 And it is the minimum cost.
 It's just not a unique number.
 But theta probably had some meaning for you.
 It's the coefficients of your polynomials
 you're looking for.
 Now, you're saying, OK, there's an infinite number
 of possible polynomials.
 Not all possible ones, but an infinite number
 which minimizes this.
 That may or may not be a problem for you.
 If you're trying to find the orbit of a planet,
 it's a problem in there.
 So it means you haven't taken enough measurements,
 essentially.
 All right, we'll deal with that tomorrow.
 But one way of thinking about this
 is that if, let's say, if phi is not full column rank,
 then the data is, I'll call it insufficient.
 There's a problem with the data.
 You haven't connected enough of it,
 or you've collected it in a special way which
 is hiding something from you.
 Suppose your system is described by a second-order polynomial
 or a third-order polynomial, and you
 happen to choose points which are all in a straight line
 in there.
 You got unlucky.
 You choose these points, and a line goes right through them.
 Then there's an infinite number of things
 that also go through them, if you consider, now,
 the higher-order polynomials.
 Now, every one of them minimizes the fit going right
 through the points, but it's not telling you
 what you want to know.
 So the data you've taken is insufficient in this case.
 So you might want to take more data in there.
 All right, so that's basically least squares.
 I want to give you another sort of interpretation to this,
 a more geometric interpretation.
 And you can see that this gives you, I think,
 additional insight, which you can actually
 use to derive different algorithms in here.
 So the problem we're trying to solve is minimize over theta.
 Notice I think of minimize as a verb in there.
 Min, I think of as a function.
 So I always write minimize in this.
 This is a habit I picked up from a friend of mine
 who knows a lot more about this than I do.
 So here's the function.
 We're trying n times d.
 And we're trying to minimize that function.
 One way of thinking about this, theta times phi,
 theta is a vector, phi is a collection of columns.
 So what you have here is a linear combination
 of the columns of theta.
 Sorry, columns of phi.
 It's a linear combination of those.
 Which ones do you want?
 How much of this column, how much of this column,
 et cetera, do you need?
 So what you can do is, OK, let's plot in n-dimensional space.
 I'm really good when n is 3.
 But higher than that, it's a problem.
 And actually, because I need a higher dimension for y,
 let's go for n equals 2.
 Let's plot these columns.
 So let's say I have a vector here.
 And it corresponds to, let's say, phi 1.
 That's the first column.
 Let's have another vector here.
 Corresponds to phi 2.
 Call that the second column of the two in there.
 Now, y in here lies in a higher dimensional space.
 It's an n-dimensional space.
 And n is bigger than d, in the case
 that we're going to focus on today, anyway.
 n is bigger than d.
 And so y lies somewhere out of this plane.
 So think of these two things as describing
 the three-dimensional or two-dimensional plane here.
 So y is somewhere up here, out of that plane.
 Now, I want to find the closest linear combination
 of these two vectors that comes as close as possible to y.
 What would you think it would be?
 Projection.
 That's exactly the projection theorem.
 And so, yes, you project that y down onto the plane.
 Da, da, da, da, da.
 So it comes to that particular point here.
 And then from this, this tells you
 what the theta 1 vector would be.
 This one here.
 Oops, sorry.
 That's theta 1.
 This one's theta 2.
 And that.
 And epsilon here is this.
 It's the error you have.
 So you can see that epsilon equals y minus phi times theta.
 And phi times theta is this point here.
 Phi times theta lies in this particular plane.
 So that is one way of thinking about it.
 What you're doing with linear least squares
 is projecting onto the columns of the regressor matrix.
 And you get to this point.
 So you can think of that from a separate point of view.
 And think of it, what's the property of the projection?
 How does it?
 I drew this line straight down, right?
 What was I trying to show you here?
 This hits at a right angle, right?
 The error is at right angles to the plane.
 If it wasn't at right angles, then there
 would be another point you could drop down
 and get even smaller error.
 So there's a right angle corner in here somewhere.
 It's right angles to everything on the plane.
 So there's an orthogonality.
 So epsilon is actually orthogonal to phi times,
 let's call this theta star.
 That's going to be my optimal one.
 This perpendicular symbol means that the two vectors
 are orthogonal.
 OK, so let's take that and say that epsilon
 is orthogonal to phi times theta star.
 Theta star is our optimal choice, our best choice.
 All right, so one way of writing that,
 these are both vectors in Rn, is to remove the inner product.

 So let me write phi theta star inner product with epsilon
 equals 0, means they're orthogonal.
 Are you familiar with inner products?
 OK, cool.
 That's good.
 So epsilon, though, phi theta star,
 epsilon, remember, is actually y minus phi times theta here.
 Actually, this is for our theta star is equal to 0.
 And you remember inner products are linear,
 phi theta star y minus phi theta star phi theta star equals 0.
 Or I could start writing these things out.
 Inner product, recall, is phi theta star transpose y
 minus phi theta star transpose phi theta star equals 0.
 And if you have a look here, you can
 see that what I've got is theta star transpose phi transpose y
 minus, take the theta star out here.
 Oops, no, don't do it that way.
 So this is, take too many steps, I'll get it wrong, y.
 And this term is theta star transpose phi transpose
 phi theta star equals 0.
 And there.
 And so the only way this can be equal to 0 for theta star not
 equal to 0 is if phi transpose phi theta star, so this part,
 is equal to this part.
 So these have to be equal, which means
 phi transpose theta, theta star, equals phi transpose y.
 And we've just seen that, right?
 That's the normal equations again.
 So you get directly from the projection theorem,
 you get the normal equations.
 So that's another way of thinking of the same concept.
 The reason that that might be useful
 is that rather than thinking of expressing your optimization
 in terms of a cost function to differentiate and make
 it equal to 0, you can think about it,
 oh, I have to find an error vector which
 is orthogonal to my regressor.
 And there are methods which derive solely
 from that point of view.
 These are called instrumental variable methods.
 And they essentially exploit the property
 that it's going to be orthogonal.
 Now, they both come to the same thing,
 but it lets you do a different class of algorithms
 for some particular cases.
 So it's worth having a look at.
 OK.
 Here's some interesting plots in here.
 I've given you four data sets and plotted them,
 all versions of x, y.
 There's some interesting things about these data sets.
 The first one is that they all have the same mean value of x.
 It actually happens to be y, and I've plotted it.
 So the mean of them, so average all of the x components,
 and you get 9.
 Average all of the y components, and you get 7.5.

 The variance in every case of x is 11.
 The variance of y is, what, 4.125.
 No magic number there.
 And your estimate for fitting the line a as the slope
 is, in every case, 0.500.
 And b is 3.00.
 Every one of these data sets gives you
 exactly the same fit to a line.
 Now, you might ask yourself, should I actually really
 be fitting a line here?
 If you look at the statistical data that you've got,
 the data set, from a statistical point of view,
 they look identical in there.
 The reason why this should be a little bit of a warning
 is some people just use the statistics of a data set.
 Is this a sufficiently rich data set?
 Do I have a high enough variance?
 Lots of, OK, this looks pretty good.
 When you actually come and plot them,
 it does not look very good.
 Well, you look at this one, and you say, OK, well, yeah,
 a line could be a reasonable thing here.
 There's quite a bit of noise, but a line
 might be the right thing to do in this case.
 You look at this one, there's a very precise relationship
 between x and y.
 It's just not a line.
 You're doing the wrong thing.
 You'd be much better off fitting the polynomial to that
 in there.
 This one, there is a line, but one outlier
 messed it up for you and made it appear incorrect.
 Now, this one, there's no relationship between y and x.
 But again, one outlier gave you the impression there is.
 And all of these, you get the same line in this.
 But you should not be using it for these three problems
 You can probably use it for this one.
 So this is an example published by Anscombe in 1973.
 And it was called Graphs and Statistical Analysis.
 The point he was making was, have a look at your data
 visually before you decide that you're
 going to fit a least squares thing to it
 and see what it actually does.
 Unfortunately, that message, I think,
 is kind of lost these days.
 People just put it into some big learning algorithm.
 They come up with a model.
 And they've no idea whether they've
 done the right thing in this.
 Three of these cases, you've done exactly the wrong thing.
 One of them is probably reasonable up in here.
 So think about your data in this.
 And now, when you've got a lot of it, it's really hard to do,
 really hard to visualize in this.
 But in 1973, it was clear to Anscombe
 that people were misapplying a lot of these methods
 for fitting data.
 OK, and the reason it becomes relevant
 is that these days, a lot of optimization problems
 are driven by data in this.
 It used to be that maybe 10, 20, 30 years ago,
 and more into the 1960s, that a lot of the optimization
 problems were usually for a design or scheduling
 a process where it wasn't experimental data you
 were typically looking at.
 It was some features of a process,
 a model of a system in this.
 Or maybe it was scheduling for your production plant.
 Is my oil going to arrive through the Straits of Hormuz
 to fill up the now defunct plant at Marsden Point?
 I know someone who actually, she spent most of it,
 she was a student here at St.
 It was me and most of her engineering career was spent
 solving the linear program in order to schedule the optimal
 fracking and, well not fracking, but the refining of different oil products.
 That would be a tricky problem to be dealing with right now.
 And as that's been shut down, there's no need.
 You just have to pay more.
 Okay, so here we have...
 Okay, let me get back to the original problem.
 So here the point is that I would say that more and more
 in the last decade, optimization problems are actually
 being applied to data that's come from measurements.
 This could be movie recommendations,
 it's probably one of the big ones to begin with,
 but it's data that was collected from a population,
 and quite literally, usually a population of people,
 and this is about certain behaviors and habits,
 and trying to fit models to this data.
 So as such, the data now contains noise in this.
 And so this is why we're looking at optimization methods
 that are designed to handle noisy data or stochastic data.
 Okay, let's go back to Gauss again
 and see if we can interpret some of this in terms of what he did.
 So planets essentially are conic sectors.
 You can go to Wikipedia, there's lots of good descriptions of conic sectors,
 but basically if you think of having a cone like this,
 you can slice it right through here, you get a circle.
 You can slice it on an angle, you'll get an ellipse, basically.
 You slice it through here, you'll get a parabola.
 Oops, no, you get a hyperbola, that one.
 So you'll get an orbit that comes through here,
 and you can slice it also.
 This is a terrible drawing.
 Slice it vertically through there, and you'll get hyperbolae.
 So they'll generate basically the curves that describe the movement.
 Some comets only go through the solar system once,
 they're actually traversing hyperbolae.
 The ellipses are the ones that are in orbit in this.
 So you can parameterize all of these conic sectors by an equation like this.
 It's a linear function, or linear parameters,
 times what are called monomials in second order.
 So x squared, x times y, y squared, x, y, and a constant.
 One in there.
 At least one of a, b, or c has to be not equal to zero,
 otherwise you get something degenerate, a line,
 or in the worst case, just a point in there if you can't go right through the origin.
 So these are the various things.
 You go through the parabola, it doesn't have a constant,
 it's the one that's right at the boundary of whether it comes back in or not for an ellipse.
 So you could actually set up a linear least squares problem,
 and find a, b, c, d, e, f.
 Actually there are only five of them,
 because you notice you could scale by any constant and it would still be satisfied.
 So there's only five independent parameters there.
 You could set f to be one.
 It wouldn't get you the parabola, but oh well.
 You wouldn't do too badly.
 All right.
 But the problem with this is that I could write down the equation error,
 I could set up a least squares by, say, making that equal to epsilon,
 but that epsilon doesn't actually have a physical meaning to me.
 It's just the equation error.
 How far out is this equation?
 Now because the x and y come from measurements,
 particularly, you know, they come from Piazzi pointing his telescope at the sky
 and saying the angle I'm pointing this telescope is such and such,
 crude telescope, poor measurement of angle,
 the noise is actually in the basis functions in there.
 And that causes a problem in there.
 So I've only got two or three minutes,
 so maybe we'll continue some of this a little later.
 But you could write it down as an equation like this and you could solve that.
 But if you've got noise in the x and the y,
 if you really write out,
 OK, here's how you might find the, quote, best conic sector that isn't a parabola.
 And you scale by the F,
 and then you write down theta 1, theta 2, theta 3, theta 4, theta 5, etc.
 And then you set up a linear least squares problem in this.
 And then this would be your regressor,
 with the columns of binomials that come from your data.
 Theta are the five parameters,
 one is the constant in here,
 and here's epsilon, you minimize it,
 standard linear least squares in there.
 You can solve it exactly as I've showed you so far.
 But in practice, what's really the case
 is there's some error in epsilon 1 and you square it.
 Now even if this is a random error, once you've squared it, you've got...