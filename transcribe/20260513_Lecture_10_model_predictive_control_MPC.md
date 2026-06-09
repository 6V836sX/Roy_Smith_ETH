 Let's begin, so welcome back. This was for my, I guess, last lecture to you in this
 series and you'll go back to the regular course, regular programming will resume shortly afterwards.
 But before we begin, are there any questions, technical questions or otherwise? No? Okay.
 So, covering this topic in convex optimisation, the topic is model predictive control and
 it was a discussion I had with Jeremy a couple of days ago, basically, you know, what the
 students really need to know about control systems and I'd like to think you need to
 know a lot of stuff, but in practice, there's a few things which employers would consider
 the most important things. Probably the idea of basic feedback, integral control, PID controllers,
 etc. And the other one I would say would be model predictive control in there, because
 it's incredibly popular in industry in there. So I thought we should cover that and it is
 optimisation. It's optimisation based, so I'm going to look at two particular methods,
 but first a little bit of an overview. So the key features, as I say, it's optimisation
 based, which gives me an excuse to teach in this class. You have a, because it's optimisation,
 you can set up a cost function to whatever it is you would like. And of course, you've
 got a wide range of possibilities. There's the classic quadratic state and input penalty,
 linear quadratic regulator problems, works quite well. But resource allocation problems
 can be considered as control if you've got some opportunity for feedback. If you're investors,
 maybe not at this stage, but risk, and actually you can apply risk in a wide variety of situations,
 but there are measures of quantifying risk. Financial or environmental costs from your
 control actions in there. And you can put in, of course, regularisation and penalty
 costs, and I'll talk a little bit about that as well. So you've got a wide range of costs.
 You've got constraints that you can easily put on the inputs to your system. I mean,
 every actuator essentially has limits, you know, 0 to 10 volts or something like this.
 There's some power limit, and you can get, you can't get any more out of that. States
 can have operating point conditions you wish to satisfy. Things could go badly wrong if
 you leave the operating point or some region of it. And of course, the outputs, your objectives,
 you'd like to keep them at certain levels. Chemical process control, you typically need
 a certain level of purity in the product you're producing. Otherwise, you're not going to
 be able to sell it. You know, you sell your fertiliser and it has a guaranteed minimum
 amount of phosphate or nitrogen, whatever it is, in it, and people will test it to make
 sure that you're not lying on the label. So you've got some constraint you need to satisfy.
 Other things is that, and so we'll make clear a bit, is that if you have a forecast of disturbances,
 so all processes have disturbances coming in. And if you have a forecast of those, then
 you can exploit that. So a classic example is in energy control systems, where your forecast
 can range. What's the energy use going to be over the next hours, the next days, and
 even throughout the season. So, I mean, in Switzerland, and I'm sure in New Zealand as
 well, a lot of the power, well, in Switzerland, 60% of the electricity comes from hydropower.
 New Zealand used to be higher. I don't know if it is, but it started selling out to the
 oil and gas industry. So it may not be as much as it used to be. I think it was 95%
 when I was an undergraduate. But that requires management of the lake levels over a period
 of a year, and predictions and forecasts in order to, what should the lake levels be.
 You could just let them all run down. And New Zealand, you probably could get away with
 that because there's so much rain. But in Switzerland, they manage the lake levels and
 they make predictions of the future use. And they decide what to spend now and what to
 put in which lakes. So, I mean, the largest one in Switzerland is this area called the
 And actually, the capture area of all the lakes that they have there is 10% of the land
 area of Switzerland. And they feed water through mountains and tunnels to get into different
 lakes. So they have a huge amount of control over that. And they also use it for pump storage
 as well. So it's a big system and it requires a lot of control. And model predictive control
 is sort of the primary method for handling those sort of systems. It has both feedback
 and feedforward components to it. The feedback is in fact, in a sense, you take measurements
 and you can make corrections as a result of those measurements. The feedforward is in
 this prediction of the future. And you can predict what your system is going to do in
 the future. Autonomous driving, how to turn the steering wheel to get around the corner.
 And you're making a prediction of where you're going to end up and exploit that.
 And also, you can integrate into the whole system nonlinear dynamics.
 So I've given a couple of little examples over here. So SpaceX, I'm pretty sure, uses
 model predictive control. And actually, I'm pretty sure it also uses CVX. And I know a
 couple of people who coded some of this. And that's used for landing those rockets back
 there. There's some very nice tricks for doing that. The petrochemical industry, that's a
 high distillation, high purity distillation column. And they refine oil and gasoline.
 It's one of the biggest industries. And that's a fairly difficult and precise control problem
 in that. And model predictive control actually emerged in the chemical process industries
 in the late 1970s. The reason is for some of these systems that are relatively slow,
 pulp and paper mills, for example, the sampling times are 15 minutes or an hour. And the time
 for a lot of the big boiler systems. So they were one of the first industries which had
 time to do the calculations in the 1970s. So nowadays, a lot of us have time. We get
 more calculation in the time interval. But that's a clear reason why it started there.
 Energy systems. This is a photo I took of that solar flower that's outside. About the
 day after it was installed, I think it was about two years ago, I was here. I said, OK,
 that's kind of cute. I'll take a picture of that. So I've put that in here as well.
 But basically widespread energy systems, particularly those with storage, require some form of
 prediction and storage management. And that's becoming more the case as we put inverter
 based resources into our grids. And given the renewable fluctuation in terms of supply,
 storage is the best way of handling the variations in demand. So that ends up being a very big
 model predictive control problem. OK, so now that you're sold, let's talk about the basic
 idea. So what you do, you can think of in these steps, and you probably have already
 seen an example of model predictive control. So you measure or estimate the current state
 of the system. I put an estimate here, and this is really, when you look at all the papers
 in model predictive control, they assume you can measure the state of the system. You can
 never measure the state of the system. It's kind of a fiction. You estimate it. You have
 a model of the system, you take measurements, you try and make an estimate of what the state
 is. And there are common filters that do that in an optimal way. But that's a difficult
 problem. So I did some work, a lot of work in spacecraft landing and spacecraft formations
 in the Jet Propulsion Laboratory, and worked with the people who would go on the flight
 teams, and they would say, in terms of control design versus state estimation, they said
 we put 95% of our effort into state estimation, 5% into the control design. It's the hardest
 problem. So they turn the estimator on when the rocket's on the ground, and it stays on
 for 30 or 40 years as the spacecraft goes into deep space. And they run a parallel one
 on the ground, comparing the measurements to get an idea of what are the forces on the
 spacecraft. Whereas if it's a control task, they've got a good state estimate, they just
 switch in the state feedback to do whatever task, and then they switch off again and cruise.
 So they're really focused on getting the estimator right. All of the literature typically
 ignores that, which is a little unfortunate, and I'll ignore it today, but it's a very
 important part of that. So what you do, of course, is you optimize all over your allowed
 input trajectories, and it's an entire trajectory over horizon, and you find the input and state
 typically actuation limits, operating regions, these are very typical ones, and disturbance
 inputs, the things that you don't measure, and there are always things you don't measure.
 They could be current disturbances or disturbances in the future, and you may have a forecast
 for those. Once you've done that calculation, you apply just the first input. You start
 on this plan. You go one step forward in time, and then you replan. So conceptually, this
 is what's happening in terms of a moving horizon. You have a horizon length of length
 M, and at some particular point, let's say you're at this point here, TK, so the dark
 blue to the left is the past, you make some optimization calculation of what your input
 should be over some horizon M into the future. So you say, okay, the notation I've used
 here is U to be applied, time K, given information up to time K, but you can think about, okay,
 I've got the whole trajectory running out over here, and now I apply that input, and
 you hold it constant, typically zero order hold, for the entire sample time. That might
 be milliseconds, it might be seconds, hours, days even, but you hold it constant, and then
 at this particular time, you measure again, and you get a new measurement, and you do
 a recalculation. So you don't follow the predicted trajectory you have here. You recalculate,
 and you get a new one, and then you do the first step of that. So it's a bit like doing
 a long planning process, going one step, more information comes in, and then you replan.
 And that more information coming in is the feedback aspect of it.
 Okay, so the components you need here in order to do this, and I'll talk about each of these
 in turn in a little bit, is you need a cost function. Now the important thing about the
 cost function, or one thing here, is this finite horizon M. You look M time steps into
 the future, you have to decide what M is. And you think, how do you decide? Well, it's
 really the relationship between the slow dynamics of your system, and how much actuation
 you have. So, for example, a building control system, there will be sensors in this room
 that typically sense every 15 minutes, and send the signal back to the central planning
 unit, and it will make a prediction of the appropriate energy levels. And for some building,
 actually, buildings no longer have a lot of concrete in them, I'm just kind of looking
 in Christchurch anyway, I'm just looking around, but a building, you know, a solid building
 with a fair amount of concrete has time constants that might be 24, 36, or 48 hours. They can
 be really quite slow, it can take a couple of days to get a building from absolutely
 cold up to the operating temperature. And then how long it actually takes is also constrained
 by how much input power you can put in. If you can run a PID on your building control
 system, you're paying way too much for your heaters, or air conditioners. You're operating
 them in the linear region. You never operate heaters in the linear region. You turn them
 on full for a couple of hours, and it heats the room up, then you might control them in
 the linear region. But most of the time, you're running them on the limits, full on, full
 on. If you run them on the limits, they're huge, you've spent too much money. So particularly
 building control systems, they run on the limits. So if you want to bring this building
 up to temperature at 8 in the morning when the first lecture is, and you want it at 20
 degrees C, and you're in the middle of winter, and overnight it's maybe 15 or 14 degrees
 C, you probably turn the heating on at 3 in the morning, and have it ramp up so it's ready.
 And that requires the forecast, to say what's the current temperature, is it going to be
 a hot day or a cold day in Christchurch, how much heating am I going to need, and when
 should I turn it on. And you adjust that. If it's coming from various sources, then
 there may be also time varying cost functions. New Zealand actually, how quickly do they
 change the price of electricity? I mean, Switzerland's typically a day and night rate.
 Yeah, but here I think it's faster, isn't it?
 It could be flat, okay. So you may have a time varying cost function that you're optimising
 over. So you put all of these things into your horizon. So when I did some building
 control ones in Switzerland, and we would typically pick a horizon which would allow
 us to see over the weekend, because the use pattern changed over the weekend. So it would
 roughly be M, in our case, is about 250 steps into the future, every 15 minutes. That's
 quite a lot. Some things you can get away with a lot less. But you've got to decide
 on that. And then there's some cost function you have. It's a usual cost. I've written
 it here as a cost at each stage. And you go over M stages. And there may be a cost associated
 with where you end up, a terminal cost. You may or may not have that component. So that's
 the cost function you minimise over both X and U. But there is a constraint between X
 and U. And that, of course, comes from the model of the dynamics. So you've got some
 dynamics here. I've got state, space, discrete time. And W here is a disturbance input.
 If I know it, I could use a forecast. Yeah?
 When you said you had 250 states there that they can get to your goal stage.
 250 steps, time steps.
 Okay, 250 steps.
 Yeah.
 During that time, are you looking to control two A patterns between there and the...
 Yeah, you plan the entire trajectory out. The whole thing. We'll see.
 And I guess my assumption is it would be linear unless some other constraints...
 Actually, the dynamics were pretty close to linear. But the constraints are always on.
 So our constraints in a building case were the actuation. That was a severe constraint.
 So much heating, so much cooling. And the other one is operating point limits. And they're
 During the day from 8 to 8 p.m. roughly, you wanted it between 21 and 25 degrees.
 But overnight, you can let the building temperature drift between 15 and 30, as long as you've
 got it back ready the next morning. So you could save energy that way.
 But yeah, you plan the entire trajectory. We'll see that as we go along.
 So you express your model of the dynamics as a constraint in there.
 And you may actually have the operating constraints that you have to obey, of course.
 And I'll distinguish here between hard constraints, and typically this is inputs.
 And these ones might be, you know, you only have so much actuation.
 You've got a maximum heating capability in your building. That's it.
 A maximum angle you can turn the steering on your autonomous driving.
 You can't get any more. And what I call soft constraints.
 These are ones you say, I like these, but they're not mandated.
 So that temperature constraint, say an operating point, we treated that as a soft constraint.
 That's a constraint where, yes, they say that the temperature should be between 21 and 25.
 But if it dropped a little or got a little too hot for not too long, nobody's going to be too upset.
 And so we consider it soft. It's kind of a flexible boundary.
 Or you might think of also current constraints and transmission lines.
 You have a maximum line, but it's not really the maximum.
 What it depends is how long you leave it at that temperature and how hot it gets
 before the line sags and hits a tree or something like this.
 So in those cases, you can say, okay, maybe I could exceed the limit for a little bit, but not too long.
 So in Europe, the allowed limit or supposed allowed limit is 70 Kelvin hours integrated over a year.
 So how many degrees C, if you like, or Kelvin, I don't know.
 But how many degrees are you outside your limits multiplied by the amount of time you spend outside the limits.
 And that should integrate to something less than 70 over a period of a year.
 So that's a soft constraint.
 And the other constraint we might have is a terminal constraint.
 Yeah, I want to finish up either at some specific point or at least in some set in there.
 So those are all the sort of components you might put in.
 Let me talk about two choices here for a cost function at least.
 So here I've written it as just a finite one.
 Here I've used 1 to M and I used 0 to M minus 1 last time.
 Sorry, I'm not consistent.
 So I have a cost function over this horizon in there.
 I haven't put a terminal cost, but there might be one there.
 Okay, here I have put a terminal cost.
 Here's a typical linear quadratic cost.
 Here you see basically your squared state, squared input, and a squared cost on some terminal set in there.
 So where you end up might be important.
 You want to end up in a position that's not too bad.
 You don't want your optimization to kind of drive you into a corner that you can't get out of in there.
 So one of the issues that comes up here, and this is the reason for putting a terminal set or a terminal cost,
 is to try and guarantee what's called recursive feasibility.
 So when you solve your optimization problem and you get a solution, you start heading down this direction,
 you know, it will change.
 But you want to make sure that when you get to the next time point and you solve your optimization problem again,
 the optimizer doesn't come, sorry, there's no feasible set.
 What are you going to do?
 You could just run with the previous plan you had.
 It's probably not a bad idea, but you would try and avoid this situation where suddenly your optimization says infeasible
 because you're sort of stuck then at that point.
 So one of the colleagues I worked with in NASA actually got the first LMI solver certified for spaceflight in this.
 And so it was for landing on asteroids in this.
 And so he had to prove to NASA that it would never come up with just infeasible.
 And so they wanted very specific proof about this that it could be used.
 So LMI-based MPC is certified for space for some applications.
 So anyway, here's a cost function.
 One alternative is to not penalize the input but ensure that it meets certain bounds.
 So, you know, steering in a car, I mean, you worry about hitting the limits, right?
 You can't exceed the limits, but there's no cost to how much you've turned the steering wheel, really.
 Whereas energy in a building, yeah, there's a cost to that, right?
 You'd like to keep that as small as possible.
 So it depends.
 You might have R equals zero or you may have a cost to that.
 Now, the cost could also be linear, and this is sometimes known as economic MPC.
 And in those cases, yes, it is, you know, it does sort of suit the idea of cost in terms of dollars,
 linear function of the state or the state in the input.
 So you can think of energy cost, probably linear cost would be a good choice for that.
 Deviation from the desired state, quadratic is usually a pretty good choice.
 So you pick a cost function.
 And now you turn the next one.
 So we've got a cost function.
 Let's look at what do we need to do for constraints.
 So you can write out like this all of your equations that you would get over the horizon.
 And you see, of course, the first one here is state time one is A times time zero, B times the input there,
 and whatever disturbance I had as well.
 So that gives you this equation.
 And then you can just keep going.
 This is just applying all of the equations up to time M minus one.
 And now you can take all of those equations and exactly stack them into a matrix equation.
 So I've taken each one of these.
 So here, take the x1 across to the other side.
 So you get minus x1 plus B u0 plus A x0 F w0.
 And that gives you that equation.
 The next row gives you the next one, et cetera.
 So you just write it down in terms of the A's, the B's, and here I've got F as the disturbance.
 And the important thing here is, okay, this is your current measured state or estimated state, if you like.
 And these disturbances, you might measure them or you might estimate them.
 At the current time, you might be able to measure at least this one.
 So in a building control, your current disturbances would be the ambient temperature outside,
 the occupancy of the room, how many people are in here, have a CO2 measurement.
 It probably does have a CO2 measurement to estimate the number.
 So it changes the air circulation in the room depending on how many people.
 So you may have a measurement of that, but this section is more likely to be a forecast.
 If you know nothing, then maybe it's zero.
 But you might have a forecast for that, so you can make a prediction.
 Certainly outside temperature and wind, solar radiation, in building control, you get reasonable forecasts.
 There will still be some error, but this gives you, once you're done, a linear constraint in X and U,
 where this matrix here is G, and this product of the matrix and whatever I have in terms of forecasts and measurements is little g.
 So I have a linear constraint to satisfy.
 Why the separation?
 Separation between what?
 You've got A and B in one matrix, and you've got F in the other matrix.
 Yeah.
 Why the separation?
 I don't think there's a separation.
 I mean, these are the optimization variables that you're trying to optimize.
 So the X and the U are what you're looking for in your optimization problem,
 and this is the restriction to the subspace where the dynamics of the system must operate.
 And the other one is the external that you can't control?
 Yeah, you can't control this.
 So this is given to you.
 X zero is your measurement of where you are right now, your state.
 Maybe your current disturbances, if you know them, and forecasts, which might be zero.
 So actually, if you know nothing about disturbances, then you just have a column of A and zeros here and there.
 But it is linear, so at each time point, you can form this little G matrix,
 and that will tell you, going forward in time, what your X's and U's can be,
 and you'll be satisfying the dynamics.

 Okay.
 Hard constraints.
 So inputs are hard constraints here, frequently, so you almost always have those.
 And you might want to have a state constraint as a hard constraint,
 so that could be polytopic, ellipsoidal, conic, all of the forms we've already seen for constraints in here.
 I've withdrawn that solar flower again.
 This is a photo I took yesterday.
 Have you noticed it's hit a hard constraint?
 It smashed the lower petal into its stand.
 Go out and have a look at it.
 I haven't seen it this morning.
 I came in at another door, but I was coming back from lunch and, whoa, there were cones around it.
 That's a hard constraint.
 Now, I don't know who coded that, but someone made a mistake on this,
 and that'll cost them a petal in order to fix that.
 So, yeah, hard constraints might really be needed.
 You would rather go infeasible and stop than smash your equipment like this.
 I don't know why it should not have happened.
 It's amazing that it did.
 Anyway, so a soft constraint, though, I'll give you the building control example.
 You typically put a soft control state into the cost.
 So here you might have this J here might be an energy cost.
 Say it's a linear energy cost in your building control.
 You would add what's really an artificial cost for the temperature,
 and it might look like this over here where if you're in some minimum maximum range, it's fine,
 but steeply increases outside.
 So it might be that you're forced to operate outside, but the cost would be high.
 So you wouldn't be operating outside this region unless there was no other option.
 Now, it might be your disturbances just are too big,
 and actually for building control systems, they always size everything
 so that a certain percentage of the year you can't really control it.
 If it gets too hot, I was doing a building in the city of Basel in summertime,
 and the only cooling was passive cooling only allowed at night through radiators and fans on the roof.
 And then one night in summer, we had the overnight low with 29 degrees C.
 There's no way the passive cooling system can get your rooms below 25 under those circumstances.
 So yeah, we violated that constraint.
 So we paid a penalty up here.
 Well, we didn't actually pay a penalty.
 The building owner was a little uncomfortable,
 but they recognized there's not much you can do under those circumstances.
 But at least the optimization didn't say, sorry, problem's infeasible.
 So this gets around the issue of infeasibility.
 That should have said infeasible shut down.
 But a building shut down and said, okay, it'll get hot.
 So the way to deal with these self-constraints is to put them into the cost function.
 So penalize the things you don't want to have happen.
 Okay, I took a little bit of terminal constraints.
 Here you'll find a lot of discussion in papers about terminal constraints
 because the bottom line here is their primary use is to prove recursive feasibility and closed-loop stability.
 A lot of people in the industry never use them because, you know,
 I don't care about proof the system's running.
 So it's easier to do the implementation without these things,
 and frequently they're not done.
 If you have a long enough horizon and things are pretty good over this horizon,
 adding a small cost at the end is probably not going to make too much difference.
 It would give you a theoretical proof of stability or recursive feasibility.
 But it does amount to specifying an end point for the trajectory.
 It really depends on your problem.
 I mean, in autonomous driving problems, you probably do want a terminal set
 and it should probably be on the roadway, right?
 You really want to make sure you don't end up off the side.
 That's not a self-constraint.
 So you can either specify the terminal set or you can specify a terminal value.
 You want to drive the state to zero, but that's pretty extreme.
 A more common one is to say it's a terminal set,
 and you would choose that set primarily so it's invariant.
 What I mean by that is if you have some control system on it,
 or at least you know a control system, a state feedback controller,
 which would make everything in that set stable and not hit the bounds.
 So stay within the bounds and stay within the terminal set.
 That's what I mean by invariant.
 So you know a control action you could apply,
 which will keep you in the terminal set, and it won't saturate any bounds.
 So effectively what this means is you're back into a linear region.
 Now it doesn't mean you actually ever get there.
 It just means that if you got there,
 then I would just be able to turn a linear controller on
 and control the system absolutely fine.
 But it's the existence of that that lets you say
 that I'm always going to be able to solve the problem.
 So you may or may not have a terminal constraint.
 It's a very problem descendant.
 Okay, so once you've done that,
 your optimization then, here's the simplest case,
 and actually it's pretty common.
 You minimize over some linear quadratic cost over some finite horizon.
 You have a linear constraint for the dynamics,
 and that might include forecasts
 because, of course, this g will depend on your current measured state
 and any forecasts you might have.
 This part, this g won't change.
 Capital G won't, but the small g will change over time.
 So you have this constraint for your dynamics,
 and you almost certainly have some hard constraints for your input.
 So this is a QP in there,
 and you can solve it at incredibly high speed
 with this OSQP software, if you like.
 It fits very quickly into a loop.
 And the question of incredibly high speed,
 when I, about 15 years ago,
 there was a PhD student who really wanted to know how fast
 he could make these things go,
 so he actually built MPC systems that he could run at over a megahertz.
 That's pretty fast.
 Now, they were limited to about three or four constraints,
 and only constraints which were just strict limits,
 what were called box constraints.
 You just had yes and no,
 because in doing the optimization,
 you had this method of projecting back into the feasible space,
 which was easy to calculate if you have just limits on your actuators.
 Yeah, but it ran at over a megahertz.
 There's not that many MPC problems that you need to run at a megahertz.
 But anyway, showed it as possible in there.
 He used programmable gate arrays
 in order to implement the MPC controller in there,
 but it was optimizing the code to get it done.
 So, yes, you could have that.
 Okay, so that works.
 So, actually, I should say,
 that's the absolutely standard MPC approach in here.
 Now, in nonlinear systems,
 you might have a nonlinear constraint in here, in that case,
 and that would obviously mean that this quadratic solver
 wouldn't be your solver of choice,
 but you might use something like Mosaic or CPLEX
 or other commercial solvers are fairly common
 for attempting to solve those problems.
 So, for linear systems, this is the way to go,
 but it's easy to extend to nonlinear systems,
 but you end up with nonlinear constraint at that point,
 what your dynamics are going to do in there.
 And that's the way everyone uses,
 almost everyone uses MPC this way.
 There is another alternative I want to show you,
 just because I think it's kind of cool.
 It's not quite as practical,
 but it really ties in a lot more with optimization.
 You say, well, how can it tie in more than that?
 I'm looking at an optimization problem here, right?
 It's what's called explicit MPC.
 A person came up with this idea about 25 years ago,
 actually in my lab, but I wasn't there.
 I can't take any credit for it,
 but it was a previous PhD student.
 And so, this uses something called parametric optimization.
 The idea is to solve the optimization problem,
 but essentially think of it in symbolic variables.
 So you can write down your solution in a symbolic form,
 or parametric form,
 and it leads to an explicit control algorithm.
 And the control algorithm depends on where you are in the state space.
 It's not linear in that sense,
 but it is piecewise linear, or piecewise affine.
 So there's a nice theoretical proof that doing this
 could lead to a piecewise affine optimal controller in here.
 So the easiest way to explain this
 is to actually just give you a simple example of it.
 And you can see why it works,
 what happens, and what the biggest problem is.
 Okay, so I'm going to use just a one-step-ahead quadratic course.
 My horizon is one time step.
 It's pretty myopic.
 I don't see that far into the future here.
 I'm just going to say, where am I going to go next,
 and satisfy my limits.
 I'm going to have some input constraints,
 upper and lower bounds, down there.
 And my objective, not in terms of the cost,
 but what it is I'm trying to achieve,
 there's actually a typo here,
 I want to find some sort of state feedback.
 Or at least more generally,
 some u is a function of x of k,
 and I want to figure out what that function is.
 I've already told you it's going to be
 piecewise affine function.
 So we'll show how this works.
 Okay, so how would I write the optimization?
 So in terms of if I had the measurements
 and I was going to solve it,
 actually power up my solver every time step
 and then solve this problem,
 this would be the problem I would solve.
 Minimize this quadratic cost.
 I haven't written this out in matrix form,
 but basically here I could write this out.
 Actually over one horizon, that is it.
 I'm only looking one time step.
 Okay, that's the entire constraint there.
 And then I've got a bound.
 All right, so there's my linear equality constraint.
 And I've got a linear inequality constraint,
 or two of them actually.
 One for the upper and one for the lower bounds.
 And I've solved that problem.
 So this is an easy problem
 to actually solve in closed form, kind of.
 So from the Lagrangian,
 you're familiar with that process.
 So I have Lagrange multipliers,
 lambda u for the upper bound,
 and then lambda l for the lower bound.
 And then you can see my cost function in here,
 one step ahead.
 So here's the Lagrangian.
 Now substitute in the dynamics to get the next line.
 Substitute dynamics.
 So if I substitute the dynamics in,
 this xk plus t, t is just one here.
 Yeah, should be one there too.
 I don't know.
 Typo, sorry.
 I'm going to blow that up and fix that.
 That's a one.
 Okay.
 Substitute in for xk plus one
 and then expand it a little bit,
 and you can see that this becomes the cost function.
 A little bit of manipulation.
 Here you've got a quadratic cost in u,
 and here you've got x,
 and then the cross term with both x and u in it.
 And here are the parts from the Lagrangian of the constraints.
 Now differentiate that.
 Look at the KKT conditions,
 but we'll just differentiate with respect to u first,
 and I get this equation
 that has to be satisfied at the optimal solution,
 setting that equal to zero.
 Now that's not the only one.
 There are, of course,
 I want to be able to find out
 the complementarity constraints
 associated with the Lagrange multipliers.
 And you know that either the constraint is satisfied
 and the multiplier is non-zero,
 or the multiplier is zero and the constraint is not active.
 So there are only two multipliers,
 one for the upper bound,
 one for the lower bound,
 and they can't both be active at the same time.
 The input is either, if it's on one of the bounds,
 it's either on the upper or on the lower,
 or on neither.
 So there are three cases.
 So the complementarity gives me these three cases.
 The first case, basically,
 I'm going to look at is
 lambda u is greater than zero.
 That means it's on the upper bound,
 so uk is the u upper bound.
 And at the optimum, this lambda u is positive.
 So now take this condition
 and substitute in that case,
 and you can see I've got this.
 So there's no lambda l in it
 because it's zero.
 Here, that's zero.
 And here's the lambda u,
 and I know that to be positive,
 by definition, at the optimum.
 So actually, at the optimum,
 this is satisfied.
 So take the less than or equal to there,
 and I get this constraint here.
 And if you have a look at it,
 it's a matrix times x
 less than or equal to some constant,
 which depends on the upper bound.
 That's a hyperplane constraint in state space.
 So in my state space,
 if I satisfy that hyperplane constraint,
 I should be running on the upper bound for u.
 Do the lower bound the same way.
 Take the KKT condition that I have here,
 and this case, I've got the lower bound active,
 so u lower bound is on.
 And now substitute that in,
 so u lower bound is there.
 And now rearrange,
 and I get another hyperplane constraint.
 It's a different region.
 It looks kind of similar,
 but the signs are slightly different.
 Actually, the bounds are different, primarily.
 So another region of the state space
 where if my state satisfies this constraint,
 the optimal solution is to be at the lower bound.
 And there's one last constraint,
 and that's when both of the Lagrange multipliers are zero.
 And there, u will fall somewhere in between.
 It will be between the upper and lower bounds somewhere.
 But again, applying that gives me this condition.
 Notice, putting the Lagrangian, I've lost,
 I don't have these lambda u, lambda l's,
 so I just have that equal to zero,
 and I write that out.
 And here, assuming I've only got one input,
 so I divide it rather than taking the inverse,
 I get a relationship between u and x
 to satisfy this,
 essentially, Lagrangian equaling zero.
 And this, of course, is a feedback control gain.
 This is some k, right?
 u equals kx.
 Okay?
 So I have three cases here.
 On the upper bound, or on the lower bound,
 or in between, and when I'm in between,
 I use this feedback.
 And that is an optimal solution
 because it satisfies all the KKT conditions.
 So you build the solution from the KKT conditions in there,
 and you see what that does.
 It splits the state space up into regions.
 And in each region, there's some function.
 Now, this one is very simple.
 It broke into three regions.
 On the upper bound, state feedback in the middle,
 or on the lower bound.
 If I take anything more complicated,
 I end up with more regions in there
 and slightly more complicated relationships.
 But you can do that in principle for any of them,
 and they are actually optimal solutions
 because they satisfy the KKT conditions in that.
 So what I've done is I've worked out
 actually what the control gain is already.
 So at each time step, I don't have to run an optimizer.
 I just have to decide which of these regions I'm in
 and then apply the correct control.
 Upper bound, state feedback, or lower bound.
 One of those two, or one of those three options.
 So that's exactly how it works.
 I've just coded up a simple example.
 Two-state system.
 So here's my A matrix, the dynamics.
 So I've got two stable poles.
 This one's faster than this one.
 I know what the eigenvalues are because it's triangular in there.
 Here's the B, Q.
 Oops, there's a typo in Q.
 The two is over here.
 I care about errors in the first state
 five times more than I care about in the second state.
 I don't care too much about the input.
 That's the quadratic penalty on the input.
 And here my upper bound and lower bound
 are going to be plus or minus 0.2.
 And this is the optimal solution
 written out as a controller.
 So if this constraint is satisfied,
 then I should just put in my maximum.
 If this one is satisfied,
 notice these are mutually exclusive.
 The signs have changed on it.
 I put in the lower bound.
 And if neither of these are satisfied,
 here's my state feedback.
 That's my optimal controller.
 Now when I come to implement that,
 I just have two if-then-else statements
 and one multiplication.
 So I decide, am I in this one?
 Nope.
 Am I in this one?
 Nope.
 Okay, multiply by that.
 Optimal solution.
 Or if I suddenly hit one of these,
 yes, do the max, do the min.
 So those are the, as I say,
 you do the work offline.
 You solve the problem like this offline
 and you decide what to implement online
 and you can make it incredibly fast
 because you're not running the optimization problem.
 You're doing what?
 Maybe you run two, three, four, five, six,
 six or seven flops.
 You really can go quickly in that.
 And if I try this out,
 here's my example.
 Let me just focus on the trajectories.
 I'm comparing two trajectories.
 This isn't a phase portrait viewer.
 It's in state space.
 So I've got X1 on this axis,
 X2 on this axis.
 The origin, not so easy to see,
 but it's right in here is the origin
 where we're trying to get to.
 And let's put my initial state X0 at this point.
 Now the optimal one where I have no constraints
 is in blue.
 It comes around here.
 The one where I have constraints,
 so I saturate.
 In other words, I hit the constraint.
 This is the trajectory.
 And then on this side,
 whoops,
 you can see how these go.
 The blue one is the one with no constraints,
 and you can see I've shown it here.
 And the magenta one is the one with the constraint.
 And actually, yeah, it takes a little bit longer,
 but not much in order to really settle down.
 And so you can see the magenta trajectory for the input.
 It's on the constraint,
 and it does state feedback to do the final closing in.
 Whereas if you had no constraints,
 this would be the optimal.
 There's a lot more action in it,
 but it doesn't get you there a lot faster.
 So anyway, that's the solution for that.
 It's an MPC problem.
 It's what's called explicit MPC in there.
 And you can probably see what the issue is already,
 partly with the fact I've used only one input
 and one horizon step.
 And then I get a nice three-zone solution.
 It's rather hard to do it.
 Well, it's not hard,
 but what happens is essentially
 you can easily do more complicated forms of state feedback
 on polytopic regions of the state space in that.
 You can introduce many more cost functions,
 longer horizons, stability, terminal constraints.
 None of that's an issue.
 You can add more and more state constraints
 or different state constraints.
 Not an issue.
 Here's the issue.
 The number of polytopic regions you end up
 grows exponentially in this.
 So if I take this double integrator,
 which is very close to the example I had,
 and now I have a horizon of 10,
 and actually I'm putting penalties on the infinity norm,
 so maximum magnitude rather than quadratic,
 but that's not a critical thing.
 Bound of 1,
 a state penalty.
 I don't want to exceed plus or minus 5.
 And now I end up with 116 regions in the state space to check.
 So at some point,
 there's a lot of if-then-elses going on
 before you decide,
 ah, I'm here,
 and then I use this control gain to calculate it.
 But once you get there,
 the other thing about those if-then-elses
 is that they can be parallelized.
 So if you have a programmable gatorade,
 you can parallelize it.
 And so each processor only has to know
 basically the edges of its constraint,
 and it just checks all of them.
 And if it satisfies all of them,
 ah, I'm the one, put my hand up,
 I have the gain,
 and then the gain gets used.
 So it could be parallelized,
 so it can be made blindingly fast in there.
 But I would only use it if I really needed it to be that fast,
 and I could get away with a relatively short horizon over there.
 But I think it's cool because of the way it uses the KKT conditions,
 okay, in there.
 But practically...
 Solvers and processors run so fast and so you can get up to a megahertz without, before you really have to do very hard work, hundreds of kilohertz, probably not so bad for small systems, but if you really have to go faster, you know, one day you'll come across an application then you spend a lot of time calculating the regions and then figure out what those should be and the whole toolbox actually in MATLAB for doing this and doing tricks like
 figuring out where you can combine regions together.
 Okay, these two are so close in gain, I don't care, I'll just use one gain in a bigger region and cut down on the number of those.
 So that's a possibility to keep in mind.
 It's more of a fun one, the one that basically when you go to industry, they're not going to want to hear about KKT conditions.
 That's the one you're going to be using in there.
 Okay, so that brings me to the end.
 Are there any questions?
 So I guess I've had fun.
 Thanks very much for listening to me.
 Regular programming resumes next week.
 But I did get the opportunity to write an exam question.
 I actually even did it before I left Zurich.
 So you have to guess from what I've presented what it's going to be.
 But anyway, okay, thanks very much.
 And thank you.
 You can hear more on modeling from data actually if you want to join this workshop next week.
 All right, good luck with the exam.
 The other questions as well.
 No problem.
 Yeah.
 I'm glad you enjoyed it.
 Yeah.
 Yeah.
 Probably could be.
 Probably could be.
 But it's still a fairly simple system.
 Yeah.
 Yeah.
 Yeah.
 No problem.
 Yeah.
 Yeah, I think they're primarily, but I think they can handle these.
 Yeah.
 Moesik definitely.
 Moesik.
 Yeah.
 M-O-E-S-I-K.
 M-O-S-E-K.
 And CPLEX.
 C-P-L-E-X.
 C-P-L-E-X.
 Yeah.
 So there are often, I think Moesik is probably one of the more common ones.
 But it's commercial.
 But both of them are commercial.
 Although at CPLEX I think they do maybe, they do give free versions to universities.

 So you might be able to look at that.
 But you have to apply specifically.
 I applied for one once.
 And they said, no.
 We know who you are.
 We don't want you having this.
 Yeah.
 Yeah.
 Yeah.
 Yeah.
 Because I was just looking at how we can do the constraints higher.
 Yeah.
 Yeah.
 Yeah.
 No, you will want a nonlinear solve of that.
 Yeah, but is there a way to sort of, I mean, is there a way, like linearizing, create a
 linear system that accurately...
 You can.
 Tides are difficult because of the, once they reach the breaking...
 ...region, yeah.
 And then they slip and they actually go over the curve to the other side.
 But you could break it up into a couple of regions.
 A piece-wise linear.
 I mean, you'd probably do okay with a piece-wise linear.
 And then you have to sort of...
 The optimization is a little trickier, but it's probably, you could probably congruent
 it together.
 Yeah.
 Yeah.
 But you also have rotational dynamics with the yaw control.
 Yeah.
 That's mainly what we're looking at with the yaw break controller.
 Yeah.
 But that can probably be reconfigured, right?
 Unless you really want to drift at 90 degrees around corners.
 Well, yeah, because, I mean...
 Yeah.

 Yeah.

 That one's a...

 If you've been to a...
 Yeah.
 We've got a...
 I need to find out...
 Just the yaw rate controls, the TIDs.
 Yeah.
 What I'm doing...
 One example with the...