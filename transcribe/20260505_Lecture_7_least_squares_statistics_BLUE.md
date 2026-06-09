 Okay, let's begin. I think it turned 11 o'clock on my dial here. So welcome back. But before
 I start, I want to ask if there are any questions from yesterday. Anything cleared up? Curiosity?
 Or anything like that?
 I have a question.
 Yeah, sure.
 So besides the rhythms, we had the geometric interpretation.

 And just a final tip really in the working, which I have a question about, is it, are we dividing both sides?
 Oh, essentially, yeah, I see what you mean. At this point here.
 So you've got this equation that's come out. Now, if theta is not 0 here, the only way you can make this whole thing equal to 0 is if this green piece equals this green piece, because the theta is multiplying both sides here.
 So you've got to make those two equal so that they subtract. And then when you write down that they're equal, take one to the other side, you get exactly that.
 Okay. Any other questions?
 All right. So we didn't quite finish last week's lecture. Not last week. I have a much more relaxed schedule than Zurich.
 So yesterday's lecture. So let me jump in and just do the last part, which is kind of the most fun part. So we can't possibly miss that.
 But basically, what did Gauss do?
 So Gauss' starting point for finding the orbit of spheras was to take Kepler's laws of planetary motion, which Laplace had applied earlier to Newton's method and showed that the gravitational laws that Newton had come up with would actually yield elliptical orbits.
 So that was known. And these are the three, quote, laws from Kepler.
 Physicists like to produce laws. Engineers consider them models. They'll always get better eventually.
 So these are the laws of planetary motion. You've probably seen them all before.
 So planetary orbits are ellipses with the Sun at one of the foci.
 So I'm sure you're aware of that one.
 Or a line drawn between the Sun and any planet sweeps out equal areas in equal time.
 So the further away, the slower, the faster coming around.
 And here's this third one, which we're all really familiar with.
 The ratio of the orbital periods of two planets is equal to the ratio of the cubes of their major semi-axes.
 Did you know that?
 So that was an observation by Kepler.
 But actually, it tells you basically how the period of the orbit you can expect on them.
 So he took these equations and then used least squares.
 But it's a nonlinear least squares problem he was dealing with in there.
 So a little bit about orbital mechanics.
 So an orbit is defined by six variables called the orbital elements.
 Five of them are position variables and one of them is a time variable.
 So there's kind of a bit of a picture here, but it's rather hard to see.
 So essentially, if you think of we're sitting on the ecliptic plane,
 so Earth's orbit is in this particular plane.
 There's an axis defined.
 It points to the vernal equinox.
 And so I guess it's in the direction of Pisces on the 18th of March or 20th of March.
 And so that defines sort of one of your axes.
 And the long axis of the orbit of Earth is the other one.
 So you've got this orbital plane.
 Now you have to think of...
 Are you familiar with Euler rotations?
 Maybe, maybe not.
 So you have to think about rotating about one of these axes.
 So the first thing you do is take the plane of Earth's orbit,
 then tilt it up about that y-axis, if you like,
 and then rotate it about its tilted z-axis and it goes around in there.
 And so now you've got the plane at a different orientation to Earth.
 I'm drawing it like this, but of course actually it's not that different.
 But it's rotated.
 And now you've got an ellipse in that plane and you have to rotate that ellipse.
 So you get three variables.
 You have to sort of twist it around a certain amount.
 And two more come from the size of the ellipse.
 How long is it?
 You can measure the two components or you can do eccentricity.
 There are a variety of ways.
 But you've now got five variables that say where you are.
 And the last one, called the true anomaly,
 is essentially the time variable.
 When Earth's orbit is at a certain point at a certain date,
 then where are you on the orbit of the Earth?
 So those are the six variables.
 I mean, there is kind of a standard.
 There's something called J2000,
 which is sort of the position of all the planets in the year 2000 exactly.
 And it's used as a reference in modern time.
 I don't know exactly what Gauss was using as a reference back then.
 But those are the six variables you're looking for.
 So the dimension you're looking for is six variables.
 Once you have that, you know where the orbit is in space.
 And you know where along that orbit the planet is.
 And now when you have to translate that back to what you would see on Earth,
 you have to turn that position into a projection of two angles.
 Where would it be in the sky?
 At least on Earth you measure the angles the same way as you define the axes.
 So astronomers measure from their thermal equinox.
 Okay, but that was the approach.
 It's already pretty complicated.
 Then what he did is he selected three observations,
 wisely chosen, the first one, the middle one, and the last one in there.
 And he calculated a nominal orbit.
 So three observations is six measurements,
 because there's two angles for each.
 And he has six unknowns.
 So he can get a unique solution for this.
 Now, it's not so easy to get a unique solution.
 This is kind of a fairly highly nonlinear system to work out.
 So he did pretty well.
 But with six equations and six unknowns,
 he generates a solution which is a nominal orbit of that.
 Of course, he hasn't used most of the data yet.
 He's just got a starting point.
 And now he did a Taylor series approximation of that
 in order to, there are nonlinear differential equations
 he had of the motion.
 And then he used that and calculated the Jacobian of that
 in order to update the orbit.
 And so he did a metric procedure.
 I'll give you a bit more details, but that's the basic idea.
 So he adjusted the linearized version of the orbit,
 so he minimized the sum of the squares of the errors
 in all 22 observations.
 If you only take three observations, the error is zero.
 But of course, there's a lot you've missed out.
 Once you put in all the data, you've got more errors.
 OK, so this is sort of the basic idea.
 He calculated what this function was.
 That was his model there.
 The nonlinear mapping taking these five unknowns
 and the current time, or whatever time he'd like to predict for,
 and comparing to the observation.
 It's a function with six outputs in there.
 And his cost function, sum of the squares.
 They're divided by two, we often do,
 so that when you differentiate it, the twos cancel.
 But it doesn't matter.
 And then he was attempting to minimize it.
 Find the argument that minimizes the cost function.
 So he took one nominal orbit.
 I've shown it here.
 Much more curved than he was dealing with,
 but this is the idea.
 And then once he had that nominal orbit,
 for all the others he could calculate an error.
 And then he iterated to reduce that error, all of them.
 Quickly, how he did it.
 So here, it's a technique I'm sure you've seen already.
 Yeah, probably.
 This is its sort of first use.
 So he took that nonlinear function I've written as h,
 and he did a linearization about his current estimate
 for the variables.
 So initially, that was the orbital element he had
 for those three observations.
 And then there's the Jacobian here,
 and then the difference between the estimates.
 So what you can do is you could define a delta theta,
 a change in the variables as the difference here,
 and an observational error, which is a delta y, like this,
 and write out your cost function in terms of delta theta
 and delta y.
 And this is what you get as a cost function.
 So here you've got the error on the observations,
 the error in the variables, squared divided by 2.
 And now we'll call that, actually,
 that's approximately equal to the actual cost function
 if you were to change the orbital elements a little bit.
 So the gradient of this function, I'll call it J quad,
 because this is a quadratic approximation
 to the cost function.
 And you get it from just linearizing the linear model
 in here, because it's an error squared term.
 And so then what he did was essentially
 he solved this linear equation, which
 is the least squares minimization of this cost.
 So here's the costs.
 This is basically the change in the error variable.
 And this is the least squares problem
 that you will get to solve that.
 So this became his normal equations.
 Down to delta theta is h times delta y,
 and he found the delta theta.
 And then he used that to update his iteration,
 improve his estimate.
 Then he re-linearized, did it again.
 And I think, actually, to do Ceres,
 he did this iteration about 11 times
 to eight decimal places with a quill.
 So that's how he basically solved it.
 So he solved the nonlinear optimization.
 Least squares is basically solving the gradient update
 step in doing it.
 So he said, oh, you invented least squares.
 This is an awful lot harder than just linear least squares.
 But it's something you've probably already seen,
 isn't it?
 OK.
 So basically taking gradient steps in there,
 it's more Gauss-Newton.
 So at least his name got involved in it.
 So here's the idea of what happens
 when you look at a function itself.
 So here's your current estimate in this.
 At this point, you do a Cayley-Ceres linearization.
 And it matches the, when you do that,
 you match, of course, the point.
 But you also match the gradient at that point.
 Now, the gradient's wrong everywhere else
 because this blue line, the real cost, is not quadratic.
 It's a much more nonlinear function.
 But now that you have this, that J quad I had,
 that quadratic approximation is a quadratic
 that goes through that green point here
 with exactly the same gradient as the original function.
 And of course, it's a quadratic.
 So it turns up.
 And you minimize that quadratic, which
 is what the least squares does.
 And you get a new estimate.
 That's interesting.
 You can color that.
 So you get a new estimate here.
 And that's your next, I should say,
 becomes your new estimate.
 And you can see it's a lot closer in there.
 And then you repeat the procedure.
 And you converge to a minimum.
 So that's what he did.
 It worked extremely well.
 And then just to give you an idea, what I've shown here
 is a sketch from his notebooks in this.
 So let me just highlight a couple of things on here.
 I've typed on top something.
 But actually, it's in fairly readable German
 if you can deal with his handwriting.
 So here, at this point here, is the first observation
 of Serres.
 Here is the last one.
 So this interval here are all of the 22 measurements
 take place in this interval here.
 When Serres comes out from behind the sun,
 the sun's down here.
 And Earth's moving this way.
 Serres to come out behind the sun appears over here.
 So if you look at that extrapolation from here
 to this point to predict that elliptical orbit,
 that is really pretty impressive.
 In doing that.
 And he got it right within half a degree.
 Also shown on here are the tracks of Pallas and Vesta,
 which he also did.
 So these are all from his notebook.
 You can check out some of the references.
 Anyway, that's what Gauss did, became famous for it.
 I mean, one of my colleagues said,
 you work your entire career in this area, optimization,
 controls, and processing.
 You get to the end of your life and you think,
 you realize, finally, you don't actually
 understand half as much as Gauss already did in order
 to come up with something like this.
 So that's where least squares came from.
 And it's a pretty impressive example of this,
 of using optimization in order to essentially find out
 some physical parameters, estimate physical parameters
 of interest in that.
 OK, so that's the motivation for what
 we're doing in some of this.
 Any other questions?
 Yeah?
 Are the actual numbers available?
 Yeah, yes, you can.
 Well, he wrote this book.
 I've seen a copy of it in, well, you
 can download a copy of various pieces of the book.
 You can send me any one.
 I might be able to find the links to you.
 The university at Göttingen had a fair bit of Gauss's handbooks
 online, and you'd be able to download and have
 a look at them.
 But it's interesting.
 The handbooks are written in German, which these days,
 to me, is not so bad.
 But the actual write-up, the paper,
 and the book he published on the property,
 is written in Latin in there, because it was popular.
 Latin was the scientific language in 1800.
 So he wrote that out, and even his name.
 So it was Frederico Gauss.
 He didn't change the Gauss, but it
 became Frederico on the title.
 And you can find that.
 Now, that's been translated into English.
 It was translated by the US Navy in 1847.
 The reason is because celestial navigation relies
 on a lot of this, and they wanted to basically know
 the techniques for developing star maps
 for celestial navigation in the mid-1800s.
 So you can find that as well, and they translated it
 into English.
 I don't have a copy of that one, but I think you can probably
 get that online as well.
 No problem.
 So that's Gauss.
 That's where it comes from.
 That's one of the basic uses.
 Let me give a bit more about some of the properties
 we're interested in in this.
 So here, I've kind of summarized what we're doing.
 We're solving this constrained optimization problem here.
 Of course, we're minimizing the square error subject
 to this equation error here in the linear case.
 Or if that's the only set of constraints,
 we can just write it as an unconstrained minimization
 over here.
 And recall that it's characterized
 by the normal equations, as I showed you.
 And at least the theoretical solution
 of the normal equations is given here by the inverse of this.
 If this is rank deficient, you could use the pseudo-inverse,
 and you'd get a reasonably good result.
 OK.
 So that's what we're looking at.
 But I want to put this in a statistical framework.
 And the reason for this is that a lot of the optimization
 problems you're starting to look at these days
 involve data measurements.
 Actually, so did the first one.
 Gauss was aware that he had errors in this data.
 Perhaps he could only measure these angles so accurately.
 So we end up with actually having noise in our model here.
 In this case, this is modeling errors in y.
 If you've got errors in the x as well,
 if you say thinking of fitting polynomials or lines,
 and then in this regressor you've got errors,
 you've got errors in both sides.
 You no longer have a linear problem.
 It's no longer linear in the errors.
 And that problem is called total least squares.
 Errors everywhere, essentially.
 But we'll focus on this one, the standard least squares.
 Now when you solve an optimization problem,
 someone gives you a bunch of data,
 and you solve this optimization problem,
 you get your parameters theta,
 you get a result called theta hat.
 That's an estimate.
 There's some underlying true parameter.
 But it's statistical.
 And the reason it's statistical
 is because the errors are statistical.
 So you can think of the error
 as it comes from a certain distribution.
 We'll assume Gaussian distribution in there, typically.
 And that means that the result
 is a statistical quantity as well.
 If you repeat the experiment,
 you'll get a different estimate of that
 because you have different noise on the measurements.
 Even if you use exactly the same values as, say, x,
 y wouldn't be the same
 because the noise would be different.
 And your estimate would be different.
 So you think about theta hat
 as being a statistical variable,
 then it means you've got some questions.
 Well, what are the statistical properties of that estimate?
 How good is that estimate in there?
 If I take more data, does the estimate get smaller?
 So there are a lot of open statistical questions.
 Well, they're open to you, but they're not open generally
 because I know the answer.
 And by the end, you'll know it too.
 So let's start and look at the statistical properties
 we have here.
 Because it tells you things like
 how quickly you can expect to converge to an answer
 by taking more data.
 And that's how much more data you need.
 So there are important questions there.
 So some possible noise assumptions.
 One which we almost always use
 is that the noise is zero mean.
 So when we take the expected value, we'd get zero.
 If it's not, you could put in the mean
 as a different parameter and just add it on here
 as another parameter to estimate.
 Not a big deal.
 It's still a linear least squares problem.
 But we will assume it's zero mean.
 You might assume that on each individual measurement,
 the noises are uncorrelated.
 That's not necessary to assume,
 and I'll get to an example where we can handle correlation.
 You might assume that the variance or covariance,
 if they're not identical, is known,
 or it's bounded,
 or you might also try and estimate that.
 All of these are fairly easy things to do.
 You might assume it comes from a known distribution,
 or you don't know the distribution.
 We typically assume it comes from a Gaussian distribution.
 So those are the possible assumptions
 that the zero mean is the critical one for us.
 Actually, the fact that the variance is finite
 is also critical.
 All right.
 So how good is our solution?
 You give me some data, I give you a solution.
 There are a couple of variables of interest to us,
 and I'm describing them here in the scalar case.
 You can generalize this very easily.
 There's the bias.
 So theta zero is the, if you like, true parameter.
 We're assuming that there is a true parameter.
 There's some real...
 And that's an assumption which actually, in reality,
 isn't satisfied ever.
 I mean, reality just kind of behaves.
 We put a model on, and we say,
 there is a true value to this model.
 It's a convenient assumption for us.
 For a start, if our methods don't work
 when there is a true parameter,
 they're certainly not even going to do well if there isn't.
 So we assume that we have a true parameter.
 The bias is the expected value of our estimate
 minus that true parameter.
 In other words, as we take more and more data in there,
 and we get closer and closer to our expected value,
 you know, this convergence is something
 isn't converging to the right answer.
 And if it's not, it's a bias in there.
 The other one, of course, is the variance.
 How much is it fluctuating about that?
 And that's the expected value of our estimate
 minus the expected value of the estimate.
 So wherever it's converging,
 we're looking at the square variation we get.
 It's a variance that you're all familiar with.
 So those are the two very common ones.
 Another one is the mean square error,
 which is something like electrical engineers
 are going to have to make circuits
 and try and minimize the mean square error
 to make little filters.
 And the mean square error is slightly different.
 It's the error between your estimate
 and the true system, the true value squared.
 Notice it's not the variance,
 even though it's a squared quantity.
 The variance, you're looking at how much you differ
 from the expected value of the estimates.
 But that expected value might not be the true system.
 If you've got bias,
 that expected value is not the true system here.
 MSC, you kind of want to know,
 what's the mean square error in that?
 And so one important thing, which is maybe not obvious,
 that MSC is an expectation.
 That's if you repeated, say, the experiment,
 what sort of variance are you going to get
 in terms of the error the next time?
 So it's the expected, and that's quite important.
 And we'll see by the end of today,
 or maybe it'll have to be by the end of tomorrow,
 where this comes in.
 Now, you can do an exercise,
 and I would recommend you do it.
 It's one of these to show that the mean square error
 is equal to the bias squared plus the variance.
 You can see that if the bias is zero,
 then this is equal to this,
 and so you obviously match.
 But the non-zero bias, you have to substitute this in,
 and then go through the calculations,
 take expectations, things cancel,
 and then you should be able to pretty quickly show
 that this is the case.
 But it does have some interesting things about,
 when we're thinking of an objective,
 what should we minimize?
 Should we minimize the variance?
 That's reasonable.
 Should we try and make the bias equal to zero?
 Also a reasonable thing to do.
 Or should we try and minimize the mean square error?
 You can kind of get not all three at the same time,
 and they're all different in there.
 Well, it could be different.
 Sometimes you can get two of them together in there.
 But there's a choice to be made.
 What are you most interested in?
 Do you want it to be unbiased?
 Well, investigate a little bit,
 because it makes a difference to how you do
 least squares estimation,
 or the optimization problems behind it.
 Firstly, if you just do standard least squares,
 with a zero mean and some variance,
 so here's a variance in scalar times the identity,
 so what I mean here is that
 certainly the expected value of EI to EJ
 is equal to zero if I is not equal to J.
 So in other words,
 there's no correlation between the noises
 on the different values of Y.
 They're all the same.
 So that gives me this.
 They all have the same variance,
 and this is the covariance matrix.
 It's diagonal.
 So you just have the same variance.
 And we're going to assume the noise is zero mean.
 What about the estimate?
 So it's not too difficult to look at what that is.
 So let's do that.
 So the expected value of our estimate
 is equal to the expected value.
 Remember how we calculate that estimate.
 That's phi transpose phi inverse phi transpose Y.
 Now also remember,
 or think that Y is equal to
 phi times the true value plus the noise.
 And now substitute that relationship in here,
 and you can see that you get the expected value
 of phi transpose phi inverse phi transpose,
 and then phi theta zero plus epsilon.
 And now you can see what happens
 when you multiply these things out.
 So if you multiply this term through,
 you can see you get a cancellation there,
 but not there.
 So it actually gives you theta zero.
 I'm simplifying this just because
 I've taken a couple of steps here.
 phi transpose phi inverse phi transpose epsilon.
 Now, so I've got the true value here,
 and now there's the expected value of this,
 which is a fixed matrix here
 multiplied by epsilon and epsilon zero mean.
 So expectation is a linear operation,
 so that's equal to theta zero
 plus phi transpose phi inverse phi transpose
 times the expectation of E,
 and we said it's zero mean.
 So the fact that it's zero mean
 means that this piece is equal to zero,
 so you just get theta zero.
 So it's unbiased.
 So if you keep repeating that same experiment,
 new noise every time,
 the expected value,
 taking all of these experiments,
 is equal to the real value.
 So you have an unbiased estimate,
 and that's very nice for a lot of things.
 So if I asked all of you to make some measurement
 in there of the same thing,
 so maybe the width of your desk,
 you can do it in calibrated hands if you like,
 and then measure how wide is your desk.
 And let's assume that you can make
 an unbiased estimate in there.
 Of course there's going to be errors.
 You've all got slightly different hands,
 and you're probably not going to know
 how should you round up the last joints or something like this.
 So you'll get slightly different things.
 We'll assume there's zero error noise.
 Now if I want to know how big the desks are,
 and I'm assuming they're all the same width,
 at least this direction here,
 I can take all of your estimates
 and average them together,
 and I'll get a better one in there.
 But that only works if they're all unbiased estimates.
 If I have bias,
 then I'm just adding,
 I still get bias,
 you've all got different biases in there,
 and those don't cancel to zero when you average them.
 They may or may not.
 They probably won't in there.
 So if I have an unbiased estimate,
 I can combine a lot of other estimates together
 and get a better one in there.
 So that's a big benefit of having unbiased estimates in there.
 So least squares has that property in there.
 I could calculate the variance for you
 by using exactly the same substitution,
 but now I just go to the definition,
 but I'm not going to bother
 because it will take us quite a while.
 So I could just write it down.
 The variance is equal to the original variance here
 times theta transpose theta inverse.
 So this is, of course, a matrix.
 So what I end up getting here is the covariance matrix.
 It's a matrix if I'm looking for more than one parameter.
 If I'm looking for one parameter,
 it's just the variance in there.
 Notice it depends on that regressor,
 and that regressor depends on the values of x.
 If we say fitting a line or fitting a polynomial,
 we've got values of x in there.
 The other thing is it's basically,
 the size of this is one over the norm of x squared.
 So if I use bigger x,
 then the variance gets smaller.
 I'm still unbiased no matter what size x I have,
 but the variance gets smaller.
 So what that means is essentially what this is
 is the inverse of the signal-to-noise ratio
 for, I guess, most of you are electrical engineers.
 So here's the variance of the noise,
 and this is the size of the input,
 which is correlated to the size of the output.
 You put double the input in some linear system
 where we're just looking at a slope, double the output.
 So your signal-to-noise ratio is halved.
 So essentially, the variance is really just telling you
 the inverse of the signal-to-noise ratio.
 So that's the standard least squares,
 and these are very nice properties.
 So let's estimate the slope of a line in here as an example,
 and you can see how all of these pieces work together.
 So let's say I've got a line where I've got a couple of points.
 Let's say I've got an x point in maybe three different places,
 and then corresponding to that, I've got some data point.
 Maybe there's one up here.
 Maybe there's one down here.
 Maybe there's one here.
 There's a couple of ways of thinking about it.
 One of the ways of thinking about it is that what I have here
 is there's sort of an epsilon here.
 This is point one.
 This is epsilon one, epsilon two, and epsilon three here.
 So I've got errors from the true system,
 but now I've got this noisy only three points here,
 but I'm trying to estimate that line.
 It's a line that goes through the origin,
 so there's just one parameter.
 What's the slope?
 Now, I can think of this as a least squares problem.
 I take my points, and I form that vector.
 I'll form it as a least squares problem,
 but there's another way to think about it,
 which is really useful for us,
 is that if I take each one of these points,
 each one of these points gives me a line.
 So I can think of the line going through the first point like this,
 and this has a slope.
 So let's call this slope theta one,
 and a slope of the first one, if you like.
 A line going through the second one has another slope,
 slope theta two,
 and maybe a line going through this third one
 has slope theta three.
 So you can think of each xy pair defines a slope.
 The slope is just the ratio of yi over xi,
 so that's my ith estimate of the slope.
 Now, another way of getting an estimate of the line
 is I could just take these estimates of the slope.
 They're all unbiased estimates
 because there's a zero mean error between the true slope
 and the one I have in there,
 and I could ask, okay, why don't I just average them?
 They're all unbiased, I can average them together.
 And actually, you can average them together.
 So I could just take those three slopes,
 sum them up, divide by three, I'd get another answer,
 which would be a pretty good one, maybe, in here.
 Depends how big the noise is.
 And that would give me another estimate.
 So I could think of just averaging,
 and, you know, when you think of averaging,
 you really sort of, if I've got r estimates,
 then basically it's one over r times the estimate.
 It's a typical way of averaging,
 and then you sum them all up, right?
 Is it the best way of averaging?
 I would argue it's not the best way.
 I'll show you a better way of averaging,
 a series of numbers together.
 And when I do least squares,
 does it correspond to the average or something else?
 Okay, so some questions
 that you're probably not curious about,
 but I'm going to pretend you are,
 and then we'll look at those.
 Okay, so let's say I've got n unbiased estimates.
 Can I combine them to get a better estimate?
 So I'll call it g, okay, I'll just call it theta here,
 but maybe I'll call my slope g hat, right?
 I'm thinking of, yeah, a gain, if you like,
 a system which might just have a gain.
 Okay, so I've got n of these g hat i,
 I sum them up, and then I multiply them by a weight,
 a positive weight in there.
 Now, in the standard quote averaging that you think of,
 if I've got n of them, the weight could be 1 over n.
 Just take them all out, I've got 10,
 add them, divide by 10.
 What's the bias if I do that?
 Now, they're all individually unbiased,
 but now I've got this calculation,
 but it's pretty easy to see that if I look at the average,
 that's the sum of these weighted individual estimates,
 it's equal to this,
 the sum of the weights minus 1 times the actual original,
 the true answer.
 So if I want an unbiased estimate,
 what do I have to satisfy?
 The sum of the weights equals 1.
 Exactly, yeah.
 So if the sum of the weights equals 1,
 then actually I'm unbiased.
 My estimate is also unbiased in there.
 Now, clearly, 1 over n is good.
 That does it.
 I've got n of them, I sum them up, I get 1 in there.
 That works, and I get an unbiased estimate.
 So just doing your standard average is an unbiased estimate.
 But there's some flexibility here.
 Some weights might be bigger or smaller than that.
 So we care about the estimate being unbiased often.
 For the example I just showed you,
 if you're measuring your desk,
 you want to be able to combine additional estimates.
 And so if we satisfy that being equal to 0
 or the sum being equal to 1,
 we keep the property of having an unbiased estimate.
 But it is a best estimate.
 It depends on what you think about it.
 What do you mean by best?
 Certainly it's unbiased.
 What about its variance?
 In there.
 And actually, in particular,
 is there a choice of weights
 that keeps it unbiased
 and makes the variance lower
 than, say, this one?
 So that's the question.
 How do we solve that?
 Optimization.
 So let's have a look at this.
 First we'll figure out what is the variance.
 So let's say we've just got the weights.
 They're going to be positive in here.
 Here's a calculation of the variance.
 I'm not going to run through it in too much detail.
 But essentially, you can see that in here
 you've got the errors in your slope.
 So here's the noise in y.
 Here's the corresponding value of x.
 Here's the x value in there.
 And there's the true system.
 So that gives you your error in the estimate.
 So that is the sum for the averages in this.
 And now, because you see,
 this is the error in our slope.
 There's the true slope plus some error,
 which is due to the fact that there was a non-zero noise in there.
 And how much error depends on the size of the x.
 And that's kind of a little bit of a clue.
 If we go back to this picture,
 would you expect the errors to be the same in the slope
 from this one or this one?
 They're not going to be the same, are they?
 This one has a lower value of x.
 It's much closer to the origin.
 And in fact, if I put an x down here,
 you'd probably just see almost all noise.
 You'd get a high variance on any estimate there.
 So this estimate has a lower variance than that one.
 I think this one's probably in the middle.
 So when I do this thing about the slopes,
 some of these estimates are better than others.
 And shouldn't I take that into consideration in weighting them?
 So shouldn't I give more emphasis on that one
 than I do on this one?
 And the answer is yes, you should.
 So you can work out what this is.
 You can see that the wg0 is cancelled out here.
 And so this is what you're left with.
 So the variance is the sum of the weight squared
 times the individual variances in there.
 And the individual variances here are not all the same
 because the individual variances are the noise on that
 divided by the value of x.
 We're estimating slope.
 And so the value of x is important.
 The larger the value of x,
 the better your estimate of the slope in there.
 So that's the variance you get in the answer.
 Now, you can take this out
 by normalizing with the sum of the x,
 and then you've got the wi squared.
 So that's what we would like to minimize in this.
 And that would give us a low variance answer.
 Well, if we can get the global optimum,
 it would give us the minimum variance answer.
 So what is that?
 So you all know how to do this, I guess.
 You do this as an exercise.
 I won't run through the calculation,
 but it's pretty easy.
 Actually, I almost do run through the calculation.
 What you're minimizing here is the variance.
 And here's that formula.
 We just calculated the variance.
 And now I'm putting in this constraint,
 which is the weight summed to one,
 and that gives me an unbiased estimate.
 So now I've got an unbiased through this constraint.
 How do I solve this constrained least squares,
 or this constrained problem?
 Well, I form the Lagrangian.
 So I've got the cost function
 plus a Lagrange variable lambda times the constraint
 equal to 0 there.
 Now, I look for the saddle point.
 So I differentiate that with respect to the w.
 I get this, and it gives me an expression for the weight.
 But that expression depends on the Lagrange variable.
 I differentiate, again, the Lagrangian
 this time with respect to the variable.
 And it basically returns the constraint
 to sum the wi equals 1.
 And so that lets me solve for, by putting this into here,
 what the lambda is and then eventually what the wi is.
 And there is a solution here.
 So I haven't worked it out.
 You can do this as an exercise.
 But this is the weight, 1 over the individual variance
 divided by the sum of 1 over all of the variances
 in the problem.
 And this estimator, this is what's
 called inverse variance weighting.
 So it's the inverse of the variance.
 So things that have a big variance,
 the inverse is small, you don't weight them so highly.
 Things that have small variance, these are valuable estimates.
 They get a higher weight.
 And this is the optimum one.
 It's called BLUE, which stands for Best Linear Unbiased
 Estimator of this.
 So the low variance estimates have greater weight.
 Now there's still some information
 in the high variance one.
 You're not throwing it away.
 You're just weighting it less than that.
 And here you can get the resulting variance.
 And this is the resulting variance.
 And now that variance decreases because if you take more data
 in here, the vector x gets bigger and bigger.
 And if they're all roughly the same scaling,
 don't do anything weird like go to infinity or go to 0,
 then this is basically, as n goes to infinity,
 this average variance goes to 0.
 Now in statistics, that's a property
 known as consistency in there.
 I said yesterday there was another meaning for consistency.
 And unfortunately, this is it.
 So when you consider a statistical variable,
 what it essentially means is that as you take more and more
 data, the probability of making a big error goes to 0.
 It gets smaller and smaller.
 So the whole distribution starts shrinking into 0.
 So it's convergence in distribution.
 So that's consistency.
 And it's a nice thing to have, of course,
 because it means if we take more data,
 we're going to get better and better in there.
 So the question is, what does the least squares one give us?
 So here's the problem with least squares,
 exactly the same problem here.
 And now I minimize this least square error.
 And this is my model in green.
 So I've got a model here, one parameter to look for.
 And we'll now do this problem from a least squares point
 of view.
 So here is the least squares solution,
 the formula I gave you.
 Regressor transpose times the regressor,
 inverted, then regressor transpose times y.
 And now because the regressor is just this vector x,
 this is 1 over x transpose x, x transpose y.
 Well, that's 1 over the 2 norm squared of x,
 then xi times yi.
 And actually, if I divide this term by xi,
 each one of these terms by xi, I get xi squared here
 and yi over xi.
 And the reason for doing that is that yi over xi
 is actually my estimate of the slope from before.
 And so I can write it out as wi gi.
 And what's wi?
 It's the size of the individual x squared
 divided by the total sum of all of the x squared.
 That's exactly the inverse variance weight.
 So least squares gives us inverse variance.
 Or I could say least squares is the best linear unbiased
 estimator in there.
 So it automatically does the right thing for us
 in terms of doing the weight.
 I could have done this calculation as I just did it
 by for each individual one getting an estimate of the slope
 and then averaging those with an inverse variance,
 but least squares does it in one shot.
 Just form that and you get it.
 And you get the best linear unbiased estimator,
 which is very nice in there.
 OK, you can even do it.
 I'll put this in here.
 It comes up a lot.
 Now, you can even do this when you've got correlated noise.
 So the noise on the second component
 is correlated with the noise on the first
 and the noise on the third, et cetera.
 So there could be some correlation.
 And so when you look at the expectation of the error times
 its transpose, this is a matrix.
 It's a column vector times a row vector.
 You get a matrix in there.
 Now, in the uncorrelated case, it
 would just be sigma epsilon squared times the identity.
 But in general, it's not.
 So use capital sigma here because it's a matrix.
 And it's a positive definite matrix.
 OK.
 OK.
 I find it interesting that the expected value of what
 are rank one matrices is full rank.
 Anyway, that's an observation.
 OK.
 So what properties do you get in here?
 If you just do standard least squares,
 you get unbiased as you did before.
 Span proof goes through exactly the same way.
 The covariance is now a little bit different
 because it has a matrix in here.
 Now, you notice if it was scalar times the identity,
 the scalar part would come outside.
 And then one of these inverses would cancel the middle.
 And you'd just be left with the answer we had before.
 So that's simplification in that case.
 But there's a formula for it.
 You can calculate the covariance matrix
 you get from your estimate.
 All right.
 But there's a question of, is it the best one?
 And the answer is actually no, it's not.
 There's a better least squares estimate that you can have.
 And this is sort of here.
 This is the particular estimate.
 So think of my estimate.
 I said it was theta transpose theta, inverse theta transpose
 y.
 One thing to note is this is a matrix in here.
 And so it's y times the linear matrix.
 If you had the same regressor, so the same x,
 but you took a new measurement, you wouldn't
 have to form a new matrix.
 You just multiply this matrix by y.
 And we'll call that matrix z transpose.
 And so the estimate is a linear function of y.
 The regressor's fixed.
 That's why it's called best linear unbiased estimate.
 So you can ask yourself, is the least squares one the best?
 Is that the best one?
 Now in the uncorrelated noise case, it is the best one.
 What about the correlated noise?
 In that case, it's not.
 The sigma squared comes up in here.
 Now notice that if sigma is scalar times the identity,
 these cancel out.
 And it doesn't appear.
 But if it's not scalar times the identity,
 they probably don't cancel.
 Almost certainly don't cancel.
 Now if you have that particular choice,
 if you really want a nice little estimate exercise
 in mathematics, which I do give in one of the classes,
 it's unbiased.
 That's fairly easy to show.
 All the same arguments go through.
 This is its covariance, and it's smaller
 than any other unbiased estimate.
 It's the smallest possible.
 So this one is the blue estimate.
 When you have correlation between your noises in there,
 if you're an electrical engineer, what that means
 is your noise has frequency content to it.
 If you're thinking of noise that comes from signals in there,
 it means it's not white.
 So it's not, essentially.
 This is the solution to white noise, if you like. But if you've got correlated noise, you have frequency content, and then you have to have this.
 But the problem here is, to calculate your best linear estimator, you have to know what that correlation is.
 And that's kind of tough. Now in an exam, someone probably gives it to you.
 No problem at all. But in practice, you've got to estimate that correlation if you want to get the best unbiased estimate out of it.
 This is about the school variant. What does it say about the matrix itself? Are you saying that the off-axis matrix is numeric? And you say that it's also positive definite. Is there some characteristic about that that you usually just see?
 Okay, I can tell you what the characteristics are mathematically, then you have to think about can you see them.
 So essentially, the off-diagonal elements are really saying that the expected value of epsilon i times epsilon j is not equal to zero.
 So if you look at white noise, you get this expectation. And what it actually is, is what's called the correlation coefficient.
 So if you have the expected value of epsilon i, expected value of epsilon j, and you look at the difference between the product of these, you get this correlation of i, j in there.
 So it means that you end up with a matrix which is symmetric because you flip i and j over, you get of course the opposite.
 So this would give you the i, jth entry of sigma i, j.
 So you end up with essentially having these, it's no longer a diagonal matrix, it could be obviously a diagonal matrix, but it has off-diagonal elements.
 And the off-diagonal elements have the cross-correlation between the two.
 Now that could be positive or negative.
 The fact that the matrix is positive definite means that for every vector, let's call it z sigma squared, or z transpose sigma z,
 think of z as a vector of the same size as your data.
 For every possible z, this product is a scalar.
 So a row vector times a matrix times a column vector is always positive.
 Another way of thinking of it is that all of the eigenvalues of that matrix are also positive in there.
 So that's what it means to be positive, it also means it's invertible, which is essential for what we want to do in there.
 But physically, it's telling you correlation in there.
 And I don't think I have enough time to really go deep into correlation,
 but there's some interesting Wikipedia-type things I'm sure you could find about the difference between correlation and independence,
 which make interesting reading in there.
 But it's telling you how much knowing one variable influences what you know about the other variable.
 If they're uncorrelated, knowing one doesn't tell you anything about the other.
 But correlated ones, yeah, you do know something.
 Could be positive or negative, you know something about it in there.
 So anyway, yes, let me leave it at this point in there so we can go.
 And I guess we'll continue this story tomorrow, same time, in there.
 But before I go, are there any questions?
 Oh, you don't have to be quick unless anyone comes in.
 OK.
 Sorry, am I going to?
 Actually, I usually don't do this.
 And the reason for that is because there is a video recording in there.
 And I'd much rather you looked at the video recording because I have an unfortunate habit of writing down things on the slide that are wrong
 to point out that they're wrong, telling you that they're wrong.
 If you only see the thing, you get the wrong stuff.
 So in order to avoid that thing, you should be able to read them from the recordings.
 Is that the case?
 You can see what's written there.
 I think you'll get that.
 So I'd much rather you heard the voice.
 I'm told that people like to speed me up to about 1.5.
 So they don't have to be quite so long in the lecture.
 Come on in.
 OK, thanks so much.
 See you tomorrow.
 Thank you.
 Thank you.
 No problem.