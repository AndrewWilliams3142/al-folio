---
layout: post
title:  A simple toy model of the coupling between the climate system and an idealized economy.
date:   2015-03-15 16:40:16
description: Useful for pedagogical purposes and for exploring sensitivity of peak warming to various uncertain parameters in ambitious mitigation scenarios.
---


Most simple integrated assessment models (IAMs) exogenously prescribe an emissions pathway, which in theory can then be modified in situ by policy parameters through the abatement rate, this limits the possibility of dynamical feedbacks between emissions, temperature and economic growth.

On the other hand, full complexity IAMs such as DICE often obfuscate the basic ideas at play by treating the abatement rate, $$\mu_{t}$$, as a free parameter which is optimised in time so as to maximise the utility function. This has a more robust theoretical foundation, however the optimisation procedure used in IAMs is often poorly documented and, as I show here, you can get interesting behaviour without taking this approach.

In `SimpleClimateEcon`, I've tried to make everything as simple as possible:

Temperatures are set by emissions using the TCRE-relationship, and temperatures then go on to cause economic damages which raises the Social Cost of Carbon (SCC) - you can think of this as the carbon tax.

The value of the SCC then sets the abatement rate (in theory, through a relationship obtained by parameterizing the output of more complicated IAMs, but for now it's just a linear function of SCC). Finally the abatement rate and the current size of the world economy set emissions for the next timestep through

$$ E_{t+1} \sim \mu_{t} GDP_{t} $$

and the circle of life continues.

<hr>

#### Example

{% highlight py %}
import numpy as np
import matplotlib.pyplot as plt
from SimpleClimateEcon import CBA

# Initialise model with default parameters
model = CBA()

# Integrate forward in time
model.forward_integration(nyears=150)

# Plot it
fig, ax = plt.subplots()
model.plot(fig=fig, axs=ax)
{% endhighlight %}


<ul>
    <li>brunch</li>
    <li>fixie</li>
    <li>raybans</li>
    <li>messenger bag</li>
</ul>

Hoodie Thundercats retro, tote bag 8-bit Godard craft beer gastropub. Truffaut Tumblr taxidermy, raw denim Kickstarter sartorial dreamcatcher. Quinoa chambray slow-carb salvia readymade, bicycle rights 90's yr typewriter selfies letterpress cardigan vegan.

<hr>

Pug heirloom High Life vinyl swag, single-origin coffee four dollar toast taxidermy reprehenderit fap distillery master cleanse locavore. Est anim sapiente leggings Brooklyn ea. Thundercats locavore excepteur veniam eiusmod. Raw denim Truffaut Schlitz, migas sapiente Portland VHS twee Bushwick Marfa typewriter retro id keytar.

<blockquote>
    We do not grow absolutely, chronologically. We grow sometimes in one dimension, and not in another, unevenly. We grow partially. We are relative. We are mature in one realm, childish in another.
    —Anais Nin
</blockquote>

Fap aliqua qui, scenester pug Echo Park polaroid irony shabby chic ex cardigan church-key Odd Future accusamus. Blog stumptown sartorial squid, gastropub duis aesthetic Truffaut vero. Pinterest tilde twee, odio mumblecore jean shorts lumbersexual.
