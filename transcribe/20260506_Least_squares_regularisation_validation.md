 Okay, I think we're beginning here, so we're already recording I suppose, so let me
 commence from roughly from where I left off last time, if this is correct. So I
 had gone through the idea of the best linear unbiased estimator for a system.
 I'll continue anyway. So I'd gone through the idea of the best linear unbiased estimator,
 and to do this with least squares, one of the difficulties of course is that you,
 to really get the minimum variance, you need to know what the correlation is between your
 estimators and that. If you just assume it's all identically distributed, then this is just
 sigma times the identity, the sigma comes out and cancels the sigma over here, you don't have
 to know, it's exactly the same estimator. So that information might be tough for you to have.
 Okay, but one thing we've established I think so far is that the linear least squares does
 give you the best linear unbiased estimator for your system, and that corresponds to actually
 fitting the data. Now what I want to point out is it doesn't correspond to the mean square error.
 The mean square error is different, and we can figure out how different the mean square error
 is by just directly deciding to optimize for this. So let's write down a different cost function in
 here, and our cost function this time is going to be essentially the bias squared. Remember here's
 the bias, and the linear least squares approach makes the weight sum to one, and so that equals
 zero here, and so this term doesn't appear, and you just get to minimize the variance. So the
 blue estimator, the linear least squares estimator, just minimizes the variance. But the mean square
 error is, did anyone do that exercise? Bias squared plus variance? So once you write that out,
 we worked out that this is what the bias is, and this is what the variance is, and now you can
 minimize it, and actually minimizing that one's even somewhat easier because it's an unconstrained
 minimization. You just have to differentiate it and set it equal to zero, and if you do that and find
 out what, differentiate with respect to the weights, which are quadratic here and here, set them equal
 to zero and solve for the weights, you get this formula here. Actually I've already annotated this
 I did that last night I guess. So anyway, you get the formula here, and it's rather similar to the
 one you had for the blue estimator. The blue estimator just had these pieces in it, right?
 Now it's got another term on the denominator, and notice it's a positive term. So the weights to
 minimize the mean square error are always going to be smaller than the ones that give you the best
 linear unbiased, and this effect is known as shrinkage. Some people are trying to adjust estimates.
 They talk about shrinking the estimates, and this is the motivation for shrinking, is you have this
 term here. So this is an extra term here. I've written it in terms of Wi, but if I multiply by
 these are the individual variances, some of the individual variances, but if I put it in terms of
 the problems and the parameters, here we've got x, some of the x, and so what this is, is that extra
 term is the variance of the noise divided by the magnitude of that gain squared. Now the problem
 with that is you don't know it. If you knew that magnitude, you'd solve the problem already. You
 try to make an estimate of, and the optimal weight depends exactly on that estimate when you're
 talking about mean square error. It doesn't depend on it if you're just talking about minimizing the
 variance or the best linear unbiased estimator, but it does depend on it if you want to calculate
 mean square error, and that's the difference between the standard least squares approach and
 deciding to minimize what you want. Now it's different, but it's very easy to get these
 confused because when you think about how you set up least squares, it was basically minimizing the
 square of the residual, you know, y minus the model times or phi times theta in there, and that gives
 you the best fit to the data in the squared error sense. Mean square error, you would think, gives
 you the best expected fit. Not the best fit to the data, but the best fit to if you had new data
 coming in, what would be the mean square error. Now you might just think, oh those are going to be
 the same, but it turns out they're not actually the same. They differ, and they differ by having
 this term here in the optimal answer. Yeah?
 When you said that it's minimizing it, or reducing it, you're not talking about the reduction of the standard deviation?
 It's the expected value of the, it's not the standard deviation. The standard deviation, you know,
 same as reducing that, it's the same as reducing the variance. Here, mean square error is actually
 variance plus by a squared. So you're minimizing both of those terms. So if you just fit the data, you minimize
 the variance, and you get an unbiased estimate. So you set this term to be zero. That gives you a, you know,
 low mean square error, but it's not the minimum one. If you allow your system to have a little bit of bias,
 your estimate's a little bit biased, and that wouldn't converge to the true answer, but it gives you the best
 mean square error. And that, I don't know, for me, that's slightly counterintuitive there. You would expect,
 you know, you minimize the variance, and you make the bias go as close as possible to the real thing,
 you'd get the best answer. But that doesn't give you the best answer in terms of expected fit to new data
 coming in. And often what we're using these models for, making predictions about what's going to happen
 when I get new data. Gauss wanted to predict, you know, eight months into the future, where would
 errors be, basically, on this. And so that distinction's kind of important to make, and it's a little bit
 counterintuitive, that getting the best fit to your experimental data doesn't necessarily, and actually doesn't
 minimize the mean square error in there. Okay, the other thing is that, as I said, the other difficulty in this
 is, of course, knowing what the best fit is depends on actually knowing the answer you're looking for in there.
 So you don't know that either in there. So how do you deal with those particular problems? And these problems
 come up, particularly, I'll show you how to deal them in the least squares, but they also come up in much more
 large-scale optimization. They come up a lot in machine learning, for example. Okay, alright. So this is the
 optimal weighting, and once I've put that optimal weighting, I can see what the mean square error is, and it's
 given by this, or I can write it out in terms of the original, or experimental variables, the noise and the
 magnitude of x in here, and you see you've got this mean square error. Now the mean square error we had before, if we
 just do the blue or the light blue squares, it's just this piece here, and it's just the variance. But now we get this
 extra term, and you notice it's a positive term. It's on the denominator, so you see the mean square error
 necessarily goes down. You do better in this. So it's strictly less than this. So here's the distinction. This best
 linear unbiased estimator, which least squares is, or weighted least squares if they're correlated, gives you the
 best fit to the data, but you have to minimize the mean square if you want the expected best fit to the true
 parameters in the system. So they're slightly different in there. So anyway, keep that in mind, and say, well, I know
 they're different. Probably I do want to minimize the mean square error. It depends. There is some value in keeping
 your estimate unbiased. It means that when your friend comes along with a new estimate the next day, you can just
 average them and do even better. So you may want to have an unbiased estimate, or sometimes you may want to get your
 expected mean square error as small as possible. So it really depends on your use case. Okay, so how do you do this? And
 this is the problem. You don't know this term. Maybe you haven't. You could get an estimate of what the variance of the
 noise is, but you don't really know what the true system is in there, or the true parameter you're looking for. So what
 you do is you create a family of estimates, typically, and you scale it by a parameter. I've used eta here, and eta is
 what's called a hyperparameter in your optimization. And so this is a, if you like, it's a tuning knob in there. It
 probably does have a correct value. You just don't know what it is. So if eta was set to this value here, the noise
 variance divided by the magnitude of the plant or theta we're trying to get, you would get the minimum mean square
 estimate, but you don't. Eta equals zero corresponds to the blue estimate. Now, we stick this eta in here so that we can
 trade off between bias and variance in there. So we can start with eta equals zero. We start at the unbiased case. As we
 increase eta, the bias increases, but the variance drops. I've drawn this on, I think, on the next page here. Here's the
 typical trade-off you get. So here's eta equals zero at the left-hand end, and if I just solve the least squares problem
 using the normal equations, I get an answer here. Best linear unbiased estimator. So any estimate I get that's unbiased will
 lie on here somewhere. This one's the best, so actually any others might lie up here. Averaging, just average all your
 pieces of data together, that will probably give you something up here. It won't be the best one, unless they all have the
 same variance. So there you've got the blue one. Now, when you put in this eta hyperparameter, what you can do is you get a
 weight and then you recalculate your average. For each eta, different weight, you could recalculate your average. And then
 what you would find is the variance drops. Now, why does the variance drop? If you make eta bigger and bigger and bigger, these
 weights go to zero, your estimate goes to zero, there's not much variance in zero, you know, it really is zero. So nothing is
 happening there. So as you increase eta, less of your answer depends on what the actual experimental data came, and more
 depends on what your choice of eta is. So the variance drops. So your estimate doesn't show the effects of noise in it
 anymore. Let's say the bias increases because now, for the same reason, your calculation is not depending more on eta and less
 on the actual data you're trying to fit. So you're getting a biased error there, and so I've drawn bias here and bias squared
 here. Now this will have some minimum at some point. I call it eta star there, so the optimal eta will be a minimum point, and that'll
 be the one that minimizes your mean square error. But when you're doing this, I've drawn these beautiful curves, which I could
 actually, no, I take that back, they're not beautiful at all. I should have calculated them more precisely. But you get these
 nice curves if you know the real answer and you can plot it out. In practice, of course, you don't. So what we do is a
 procedure known as validation or cross-validation. So you take your data you have available, and you split it into two
 groups. One group you're going to fit, you get your best fit to the data, and the second group here, we call the validation
 data set, you're going to test the quality of the first fit. So you do this, you have this set of data set aside to test the
 quality of the fit that you got from this set of data. And of course the noise on this set of data is independent of the noise on
 this, and so what you're trying to do is get an estimate of what this curve, trade-off curve, looks like. Now you don't have to do
 any new experiments. You've got this fitting data. All you have to do is run through here and choose different values of eta.
 Each time you do a different value of eta, you'll get a different weight. You put those weights in to average up, and you get a new
 answer. So you can create a grid of values here. It could be an incredibly fine grid. It depends on how patient you are with how
 much computation you have available. But you create a bit of values, and you get a whole family of possible estimates from your
 fitting data set. And then you use your validation ones to test, well, what is the square error on there, or the mean square error.
 And then you plot that tested value, and it will roughly show the same characteristics as this curve here. I say roughly because it's a
 statistical estimate. There's noise in this part as well, of course, so you never get it exactly right. So you don't measure just the
 fit here, but you also get a bit of noise involved. So it could be a bit rough, but you should see some sort of minimum, and that's what your
 best value of eta is. And then so you can use that. Now you have to be a little careful here. You might say, and actually in this case it
 would probably work for this particular problem. Is that eta going to be dependent on the length of data you have?
 You're trying to fit the data. I mean, the numbers are not going to be the same, because essentially you say you're actually fitting. It's the
 MSC of the parameter fit that you're minimizing there. So here what you have is you're trying to find the tradeoff point where you're
 getting this, knowing that the errors you have in your parameter, there's a linear relationship between your new x, the errors you have in
 the output y. The linearity is preserved, which means that the shape of the graph will still be the same. So yeah, it'll work for this. If
 those parameters were a much more difficult, you know, there's a nonlinear relationship from those parameters to the output y, Gauss's
 example, for example, or a lot of cases, then you're trying to evaluate the quality of the parameters based on the quality of the fit. You
 probably actually care more about the quality of the fit and the output than you do about the parameters. It depends what you're
 interested in. You know, if you're a physicist trying to determine some physical coefficient exactly, then you probably care about the
 parameters. But then you've got a nonlinear relationship between the errors in those parameters and the errors you see in the y
 is really kind of an important one. And it's one that requires an extraordinary amount of discipline. If someone gives you a bunch of
 data, you don't want to say, oh, I'm only going to use half of it and save the other half for testing. Your temptation is to use
 everything you've got and get your best possible fit. You just have no way of knowing if it's the best possible fit now. But it's used to
 the data. So you really need to put some of your data in reserve. You lock it away. You're not going to use that data except to test the
 quality. And the reason we're testing the quality is that there isn't just one right answer. We have to look at this hyperparameter and say
 what's the best hyperparameter. So we need to have some data available for checking on this hyperparameter. Now, choosing hyperparameters
 or forms of hyperparameters is a big deal in system identification. It's a big deal in machine learning. What are your hyperparameters?
 Here we've just got one hyperparameter in there. But in some complicated problems, you can end up with more than one. And then you have a
 or maybe in a cube. And so you can see that you're going to get exponential growth in the number of points. You don't have to do any
 additional experiments, but you do have to have a richer data set to determine exactly what the best hyperparameters are. So I'll give an
 example in this workshop. I don't know if you're going in there. We typically use two hyperparameters for identifying transfer
 functions or state-based representations from experimental data or impulse response functions. Okay. But anyway, this is how you
 in any optimization, machine learning, and system identification. And that's an idea which is called regularization. I don't know if you've
 come across this before. Yeah? Okay. One person has. And I find actually this approach, looking at least squares, is the easiest way to
 regularization. It appears in a lot of different research computational fields. And people have tuned and tweaked it to get the features they're
 interested in. But I think this is the simplest possible case. So essentially what you do is you take your typical cost function here. So here my
 cost function is really fitting the data in here. And if that's all I did, I would get the blue estimate. And now I add a term which is scaled by a
 hyperparameter, and it's some function of the parameter itself. So we're penalizing something which will be in some way related to the size of the
 theta. As I was saying, I want that to be as small as possible. Now a heuristic reason why that might be a good idea is that if it's very hard to
 determine what theta is from the experiment, the noise could be giving you a poorly conditioned result. You could end up with very large values of
 theta and think these are probably not realistic. And so you penalize the size of it to make it something more realistic. But that's a very heuristic
 approach. Here we can be much more precise. So there's some very common regularizations, what this function of theta should be. It should, in some sense,
 give you an idea of the size of theta. So a norm is a good choice. So here, probably the most common one here is just to make that the two norm squared. So it's eta times the two norm
 squared that you would put in there. And that's what's known as ridge regression in there. You can think of eta times an identity matrix. And so eta is on the
 diagonal, that's kind of the ridge. That's a term you see sometimes. More generally, you could make eta, or this function, be equal to what's really a weighted two norm for theta.
 That's known as Tikhonov regularization. You've got to have a positive definite weight, but it's a bit like a scaled norm or a scaled weight where you say some, and it's one way of expressing the fact that some parameters are more important to you than other parameters.
 But now if you've got d parameters you're searching for, r is of size d squared. Well, no, no, d times d minus one over two. It's got to be symmetric, so you only need the upper triangular over there.
 But it has a lot more parameters, which means that when you're trying to decide what are the right ones, you're in a high dimensional space. So a more common thing is to parameterize r by maybe one or two other parameters. It has the correct structure, you don't know how big it is. You might not know what some parameter is in it. But if you just say it's an arbitrary positive definite matrix, you've got an enormous computational problem, probably not enough data to give you a good answer.
 So it's a low dimensional representation.
 Now there's another one here, the one norm of this. It's still a norm, scales with the size, but now that's just the sum of the absolute values of the estimates in there.
 And if we have enough time, and I never have enough time, but maybe we'll try and make some time, I can tell you what that's useful for. Does anyone know what LASSO is?
 So that's the idea behind LASSO, is a one norm regularization. And it promotes sparsity in the answer. What it means is it will set as many of the parameters of theta to zero as it can.
 And hopefully I'll show you why that's the case, but if I don't get a chance, we'll see.
 But anyway, there are many, many choices in here, so I'm going to focus on that choice.
 Alright, so here's my problem. I want to minimize the fit, exactly as before, and now it's eta times, actually it's the two norm squared there, it's going to be on my regularization.
 And using two norm squared means I can solve that using exactly the same code I used for least squares.
 Because you see, I can rewrite this equation here in terms of y minus theta, and then I stack it up with the square root of eta times eta times theta, and if you multiply that out, you'll see it gives me exactly that.
 But it's also exactly in the form of a regular least squares problem.
 And I just solve it with, I solve it with the code I have, I write the normal equations, and if I write the normal equations down, this is what I get.
 So, eta equals zero standard least squares, eta non-zero, I get this regularized least squares.
 And you can see an immediate effect.
 So supposing you didn't have enough good data in phi, that's the x,
 then what this does is it adds an identity here, and adding the identity will be guarantees you can invert that even if you couldn't invert phi transpose phi.
 So you get the ability to invert it in there.
 And so if you're in the situation of having more parameters than you have measurements of the system,
 so you're looking for n parameters but you're after a thousand n, sorry, you're after a thousand n parameters and n is some smaller number,
 then there's no way you can invert just phi transpose phi, but you can invert the regularized one.
 So it's a big deal in machine learning where often if you have very large parameter sets for very large models,
 the only way you get solutions is by including regularization.
 But you have to kind of regularize in the right way to get the solution that you want, and this can be particularly tricky.
 It's easy to do in this problem that I showed you in here, and I'll show you why that is in a second.
 But this makes this invertible just by having a non-zero agent in it.
 It also reduces the condition number of the matrix.
 So if phi transpose phi had a very high condition number, are you familiar with the technical determinant, what a condition number is?
 No? So it's the ratio of the maximum singular value divided by the minimum singular value in this.
 If the minimum singular value is zero, in other words, it's not invertible, then it's infinite.
 But if it's big, it might as well be infinite because your answers are worthless in there.
 So you would like it ideally to be as small as possible.
 And ways to get it small here are good choices of x.
 And you remember we were measuring the slope.
 If I use big values of x, lots of big values, I'll get a nice, well-conditioned problem in there.
 But maybe you didn't get to pick x.
 Maybe that came from someone else's experiment and they didn't quite understand the principles that you do.
 And so the x is pretty poor, and that's poorly conditioned.
 Putting in regularization will improve the conditioning in that.
 Putting in too much will mean the regularizer determines the answer and not the data.
 There's some right balance in between in there.
 And that's what we use validation to find.
 But those are sort of the benefits you get from putting in regularization here.
 So let's go back to exactly the problem we've been looking at,
 which is minimize the mean square error of this.
 So here we have our fit to the data as before.
 Here we have our regularization term.
 And now this is the solution.
 Now in this simple case, so this is the solution I get from the normal equation.
 In this particular simple case, this is x.
 And so this is x transpose x plus eta, the identity minus.
 So I get this here.
 And then I can actually do the same trick of multiplying by squared and dividing by x over here to get this.
 And now I can interpret this solution here in terms of weight.
 And you see doing that gives it in exactly the same form as minimizing the least square error.
 So I go back to when I just used differentiation and set equal to zero and say,
 what was the one that minimizes the least square error?
 It's basically this one here with some parameter.
 And I call that parameter eta.
 And this was the ideal weight I get in order to minimize the mean square error.
 Now if I go back and look at the regularized least squares, it's exactly the same formula.
 So this regularization in least squares gives me a way of looking for the minimum mean square error.
 And so there are sort of two major benefits, I would say, for introducing regularization in this problem.
 There are some others, but they don't come up here.
 But the two major ones you get here is it makes your problem well conditioned in this.
 If you have poor data or you don't have enough measurements to determine the number of parameters.
 And the second one is that it lets you investigate the bias-variance tradeoff.
 It wants them to get the right bias-variance tradeoff to minimize the mean square error.
 So those two things that just standard least squares doesn't address in there.
 You just get the best linear unbiased estimator.
 If your data gave you a poorly conditioned regressor, then, okay, you get a poorly conditioned answer.
 But that's all you've got.
 So regularization is the way to address it, and those are sort of the two key features you get here.
 When you're doing other things like system identification, you can introduce the regularization in a different way,
 and it will give you other features you might be interested in there.
 But for a standard least squares parameter fitting, these are probably the basic two ones you get.
 Okay, yeah, so I think I've just written this down here because I thought it was kind of important.
 But anyway, I think it's just what I've said.
 Essentially that eta increases, the solution depends less on the regressor and more on the choice of eta.
 So it reduces the variance but increases the bias, and the minimum mean square error is somewhere in the middle in there.
 And you need validation to do it in practice to find out what the real value is, what the best value is.
 And in badly conditioned problems, so I've given an example of a badly conditioned problem here.
 So here's a regressor here, and the numbers are all pretty big.
 The regressor has 1, 1, 1 plus 10 to the minus 8, and 1 minus 10 to the minus 8 in there.
 And so if I have a measurement, y, which is 1, 1, and I put it in here, I get that the optimal theta is 1, 1.
 Okay, but if I do something slightly different, I call some y2, which is the same as y1, but it's got a 1% error in the first measurement.
 So that's out by 1%.
 I get another estimate, which is basically minus 10 to the 6 plus 10 to the 6.
 Okay, now that's what I call a badly conditioned estimate.
 You made a 1% change in your measurement, and you got 6 orders of magnitude change in your solution.
 I would be worried at this point.
 The reason is, if you look at the maximum and minimum singular values of this,
 I don't know, they're probably root 2 and root 2 plus 10 to the minus 16, or 10 to the minus 16 and root 2, or something like that.
 You'd have to power up MATLAB and figure out what it is.
 But you will find that this is incredibly poorly conditioned in there.
 And that doesn't mean that some of the numbers are close to 0 or anything like that.
 These are all extremely close to 1.
 They're also very close to being one is linearly dependent on the other.
 You only have to make a change of 2 times 10 to the minus 8, and they're exactly the same.
 And then you say, they're not linearly independent.
 How can I expect this to work in there?
 And because they're so close to not being linearly independent, that's why it basically doesn't work.
 So that's something you can sort of fix.
 I say fix.
 You'll get an answer if you put in regression here.
 But fundamentally, you've chosen an extremely poor example.
 It's as though you used, in this estimating slope, you used two values of x,
 which differed only by 10 to the minus 8, or 2 times 10 to the minus 8.
 That's just not a very good way of estimating slopes, right?
 So you might not expect, it's not going to be great.
 So you won't get a very good answer, but you will get a better answer for some value of eta in there.
 The real solution is to go back and do some more measurements in your system.
 Okay, so actually let me add another page here.
 Because what I'll do is I want to talk, let's put a page like this.
 I want to talk a little bit about this other one, just because it's kind of fun, the other regression here,
 which will be, let's say, L1 norm regression.
 So here I've got some cost function where J of theta.
 Actually, let me just do the very simplest thing.
 Let's just make it theta 1 norm.
 And I'll subject to, say, maybe some linear constraint, phi theta minus y equals 0.
 So if I look at this, this is defining, essentially this defines a line, or more generally a hyperplane.
 And now I'm trying to find the smallest 1 norm.
 Now you have to think about, well, what does the 1 norm look like?
 So what I'm going to draw here is what's called the 1 norm ball.
 So let's say we've got two components to theta.
 Let's say it's theta 1 and theta 2.
 Now this constraint here is going to specify a line in this space.
 So let's choose a line.
 Maybe it, here's my line.
 So this is the set of theta such that phi theta minus y equals 0.
 Okay, I've specified a line.
 Now I want to find the minimum 1 norm.
 One way of thinking about this, what does a 1 norm ball look like?
 So let me say what I mean by that.
 The 1 norm ball is the set of theta vectors here.
 Theta's a two-dimensional thing.
 The set of theta that has norm equal to 1.
 One norm equal to 1.
 Two norm equal to 1 is a circle, right?
 Sum of the squares of the elements equals 1.
 That draws a circle for you.
 So this would be a 2 norm ball.
 Theta, it's called a ball for obvious reasons.
 Well, actually, in the 2 norm it's obvious.
 You choose any other norm, it's not obvious, but it's still called a ball.
 Okay, so that's the 2 norm ball.
 The 1 norm ball looks like this.
 I've scaled it differently just so it's a little clearer.
 Actually, maybe I should scale it the same way because it goes through the same point here.
 So these are 1 norm.
 It's a different colour on my thing, but I don't know if you can see it.
 It's a different colour there, is it?
 No, it's a poor choice.
 Let me try again.
 Let's make it this colour.
 Okay, so this is the theta 1 norm ball.
 So everything on that line has norm equal to 1.
 One norm equal to 1.
 What's the infinity norm?
 The infinity norm is the maximum element, right?
 So the infinity norm ball is this one.
 Everything on that line has a maximum element equal to 1.
 So you've got those particular 3 balls.
 Now, if you think one way of solving this problem is to take those balls
 and just make them bigger and bigger and bigger until they touch that line,
 and that'll be the solution you're looking for.
 It's the smallest one that intersects that line,
 so it's the smallest one that gives you the solution.
 So grow these up until they hit the line,
 and in particular I want to grow up the 1 norm,
 and it hits the line like this.
 The 1 norm has this feature.
 It's called pointy.
 This is a technical term.
 You might not believe me.
 It's pointy, but it has sharp edges on it in here,
 and where it has the sharp edges actually corresponds to
 this would be some value of theta2,
 but it corresponds to theta equals 1.
 The first component equals 0.
 This one, the second component, equals 0.
 So you see that the pointy parts have zeros for the values in the other components.
 So when you grow this ball up and you hit,
 you're going to get basically something that has all of this component here
 and none of the component here,
 so it will set the theta1 equal to 0,
 and that's why we say it promotes sparsity.
 If I draw this ball in three dimensions,
 you know, I've got this like two tetrahedrals put together,
 and it's got more points, but it has exactly the same feature.
 On all of those points, one of the components is 1,
 and the others are 0,
 and now when you think about growing it until it hits that line,
 then you see that you typically get a solution
 where you've just got a one non-zero component in there.
 Now, you might, if the line was exactly at 45 degrees,
 then yeah, you would get others in there,
 but most of the time you're just getting one of them in there,
 and that's why it promotes sparsity.
 That's why it tends to return answers that have lots of zeros in the theta vector in there.
 Here, this is an extreme case because, of course,
 when you add the rest of another piece to this cost function,
 you'll modify this somewhat,
 but it does show you the effect that you're looking for.
 Another effect you have on this, this one's kind of interesting,
 is supposing this comes from data,
 and so what will happen is there might be some actual measurement noise in that,
 and I'll have a slightly different line,
 but you can see there's a whole lot of lines I could draw
 which would give me the same answer,
 so it's actually quite robust to noise in the data as well.
 Now, some of those lines might give me a slightly higher value here than there,
 but they have the feature, they all share the feature,
 that this component in this direction is equal to zero.
 You have to make quite a big change in your line,
 say something coming over here in order to get the other component to show up in there.
 So, I hope next week I'll give you an example of an optimization problem
 where this was used to minimize the number of things that you needed to change.
 We had, what, one and a half thousand control variables,
 which were difficult to change,
 and we wanted to achieve an effect with the minimum number of them changed.
 So, we regularized with the one norm,
 and rather than, you regularize with the two norm,
 and all one and a half thousand show some sort of variation.
 You think, oh, that's going to be tough.
 You regularize with the one norm, and there's only about six or seven
 that show you some variation, and the rest are all zero.
 And it's much easier to implement.
 So, I'll give you an example of that, I hope, next week.
 But that's the effect of one norm regularization.
 And so, it's used in statistics.
 It's used in signal processing for extracting frequencies from multispectral data,
 where you know that it's dominated by a small number of frequencies,
 but you don't know what they are.
 So, your search space is basically a very fine grid of all the frequencies
 with a one norm regularization so that most of them get set to zero,
 and you only find the non-zero components in there.
 So, it has a lot of use in statistics as well.
 But that's a lot of the things we do as electrical engineers.
 Well, I'll just give you an example for electrical engineering.
 You can imagine hunting for unknown frequencies in a signal.
 That's a pretty good example of a one norm.
 Two norm is essentially trying to minimize mean square error
 of some particular fit to a signal.
 That's another perfectly valid one.
 So, those are the two.
 Now, at this point, I would say, I have another whole slide,
 another whole lecture I thought I was going to start,
 but I'm not seeing much benefit in starting a bit of convex optimization,
 so I'm going to delay that until Monday.
 But what I thought I would do is sort of open up the floor
 to general questions for the last five minutes on this topic
 because we'll go more into convex optimization this time,
 and so we'll leave.
 Obviously, this is a convex problem,
 but we'll do other convex problems next week.
 Yeah, questions?
 You said earlier that least squares is the blue.
 Isn't that not always the case?
 No, it's always the blue.
 And the reason is essentially that when you do least squares,
 remember we went through a proof which showed the bias equals zero.
 And so that's the property you get from least squares.
 So, that really puts you at the eight or equal zero case in there.
 And then, once you're at that case,
 automatically your objective function is minimizing just the variance.
 So, you will always get the blue estimate for linear least squares.
 Yeah?
 You kind of described that regularization is kind of like generalizing large numbers.
 Yep, that's true.
 Is there a similar formulation for parameters with small values?
 Yeah, well, it's not similar here.
 It can be problematic in the sense that if you think of, you know,
 when we're motivating this, we're thinking of theta.
 It could be a stochastic variable.
 You get noise.
 And now, what you would like to penalize is one over theta.
 Now, if you think about the statistics of one over a variable,
 they're really a lot nastier than just the statistics of a variable.
 For example, it's possible that one over a variable is not,
 doesn't even have a mean defined because you can't integrate it.
 You can't integrate x times the probability distribution in there.
 Whereas, if it was just on the numerator, no problem whatsoever.
 In fact, the inverse of a Gaussian in there is, you know, is such a case.
 You get an example of a Cauchy distribution.
 You write down the integral for calculating the expected value.
 Can't be solved in this.
 It's not even infinity.
 It's that the integral is not well defined in there.
 So, you have statistical problems.
 But if you're dealing with, you know, values where you don't think
 that that theta is going to be anywhere close to zero,
 which is where you're going to get that problem,
 then maybe you could do that in this.
 But it would be sort of one over.
 Then you end up with a nonlinear relationship.
 It's a tougher one to deal with.
 So, one example which I'll talk about in this workshop
 will be the case where you're trying to fit an impulse response,
 which for stable systems, they're all decaying exponentials.
 And there, your regularization is essentially you're using
 something based on exponential decay
 to make sure that your answer has this property that it decays.
 So, what you do is you increase the penalty as more,
 as you get towards the tail of the exponential distribution.
 So, the penalty grows, and that forces it down.
 It gives very nice results in there, but you have to,
 you have, it's sort of, in effect, trying to force it to zero,
 sort of the other way around, but not everywhere.
 You do want to capture all the important features,
 but right out in the tail, you're probably being,
 it's noise is telling you what's happening out there.
 And so, you force that away.
 So, there are other varieties.
 And coming up with the right regularizer
 is something of an art in this.
 And, you know, you come up with a good regularizer
 for some particular problem, you'll make yourself famous.
 Or you'll at least get a PhD in the topic.
 Yeah?
 Yeah.
 Yeah.
 It doesn't affect the bias versus the variance.
 What it affects is how well you estimate where the tradeoff is.
 But, yeah, people do lots of things.
 There's sort of one and end type validation,
 where you break it up into, say, 10 samples,
 and you get best fits on a bunch of them,
 and then you use that last one to just try and judge
 what is really the best fit to the expected value.
 So, you'll see, I call this cross-validation.
 Cross-validation really means that you are using new data in there.
 But there are other ones where you try and get,
 use as much of the data you can
 and still get some sort of validation in there.
 So, if you read up on the topic,
 you'll find that there are lots of tricks.
 I've given you probably the most reliable and the best one,
 but it's really uncomfortable to not use half of your data.
 I appreciate it.
 Actually, that's a good question,
 because it really depends on how you're going to use it.
 So, in this particular case,
 we're trying to just estimate one parent with some slope.
 And so, there's no meaning to the order in which the data comes in.
 It's just another estimate in there.
 And I could put this in the validation bin
 or I'll put it in the data fitting bin in there.
 But sometimes the order of the data matters.
 So, if you're trying to, say, estimate an impulse response,
 it'd be like only estimating every second point in there.
 So, here, knowing what comes next, immediately next,
 the time information is important,
 and they should preserve that,
 so keep one chunk all together,
 and then at a later time,
 phase that next chunk away for validation purposes.
 Actually, no, because it's sort of a batch process.
 certain amount of data and then you do your analysis on that so you could collect a certain amount of fitting data and you could collect a certain amount of validation data and so often you're given just one data record because usually you don't have as much control over the whole situation as you like your boss gave you the data you know the previous intern collected the data neither really understood what was happening so you end up with some long data record and then you have to think okay is the
 order contain the information or can I just use any from any point and if the
 order contains the information how do I make sure that my validation data is not
 correlated with the data I'm fitting on because to get a good estimate there
 you're really trying to get the effect that this really is quote fresh data now
 it could be if you if you have some system that slowly decays so it's a
 signal you're looking at and it's slowly decaying away if you just cut it in two
 the first part of the validation data is going to depend on what the last part
 of the one you just saw because it's only slowly going down you might actually
 have to leave a gap and throw away some extra data because it's it's too
 strongly related to the the fitting data that came before it so there isn't well
 you know there's not a lot of good theory you could do about this you have
 to think very carefully about am I testing on data that has different noise
 uncorrelated noise with with respect to the data that I did the fitting for
 yeah oh this the one norm stuff yeah yeah it's essentially a laptop as a prime
 example of it but you can use it anywhere where you would like you have a
 lot of parameters to estimate and you would like a lot of them to be zero if
 they have very little effect then one norm regularization will get that for
 you
 yeah
 yeah elastic laptop yeah
 yeah
 this
 kind of constraint
 we can never drop them off
 so when we do the automotive feature selection
 yeah what is it drop off some of the constraints that we can never drop off
 yeah oh no no so what you you what you would do in this situation is to decide which of those
 parameters that you must have stay and don't regularize those or regularize those are the
 two norm regularization and then take the selection where corresponding to features
 features you may or may not have and then one norm regularize those you don't have to
 apply the norm to the entire theta vector you could have some values of theta are for
 things that you must have in your model and other ones are things that you might have but might not
 and then only apply the one norm to the that optional set
 and apply a two norm or some other regularization to the others
 so the theta in MSE the first term could be different from the
 it could be in the MSE problem of course it's the same but in a more general problem
 with feature selection plus other fitting characteristics then yeah they could be
 different yeah yeah i'm just curious about the way that you say that we throw away we don't use
 oh yeah we save it yeah
 if you're interested in using for the validation
 yeah yeah but each time you're sampling and not returning the value to the to the total data
 isn't that the same thing i mean because then what it amounts to is each time you run
 it's going to be a random selection of which data we can put that your
 input that you're actually using and the validation would be the same thing
 um it is if you're thinking of it running it as a process if you like i'm presenting here
 as more as a batch type of thing so i make one division of the data into two
 but yeah then you have this issue of do you return it or not
 well if it's going to be validation then you don't
 yeah that's right so if you're going to validate on what's left in there
 then yeah you would not return it so there's another another point is once you've chosen
 your validation question your number your eta for your validation should you go back
 and refit the entire data set now now that you know what that number is