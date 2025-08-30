Purpose:



**Advanced personalization for pet meal plan subscribers based on:**

1. Pet profile (name, breed, age, weight)
2. Dietary preferences (grain-free, high-protein, sensitive stomach)
3. Previous meal ratings (survey feedback)
4. Purchase cadence (monthly, bi-monthly)
5. Shipping zone (East Coast vs. West Coast)



Output:

Single template dynamically renders:

1. Greeting
2. Personalized recommendations (calorie adjustments, formula swaps, discounts)
3. CTA variations per shipping zone
4. Breed-specific dynamic image





**Handlebars Code**



{{!-- 

===============================================================

&nbsp; TEMPLATE: Meal Plan Adjustments \& Reorder Campaign

&nbsp; PURPOSE:  Advanced personalization for pet meal plan subscribers based on pet profile, dietary preferences, meal ratings, purchase cadence, and shipping zone.

&nbsp; OUTPUT:   Dynamically renders greeting, recommendations, CTA, and breed-specific images in one template.

===============================================================

--}}





<p>Hey {{pet\_name}}’s human 👋, we’ve cooked up something new for {{pet\_name}}.</h1>



<!-- Dynamic Recommendations -->



{{!-- Weight-based adjustment --}}

{{#if (gt weight\_change\_percentage 10)}}

&nbsp; <p>{{pet\_name}}’s weight has increased by over 10% since the last order. We recommend adjusting the calorie portions for optimal health.</p>

{{/if}}



{{!-- Low meal rating → formula swap --}}

{{#if (lt last\_meal\_rating 3)}}

&nbsp; <p>We noticed {{pet\_name}} wasn’t a fan of the last meal. How about trying our <strong>{{recommended\_formula}}</strong> instead?</p>

{{/if}}



{{!-- Inactive subscription → discount code --}}

{{#if (gt days\_since\_last\_order 60)}}

&nbsp; <p>We miss {{pet\_name}}! Use code <strong>{{discount\_code}}</strong> to get 15% off your next meal.</p>

{{/if}}



<!-- Dynamic CTA -->

{{#eq shipping\_zone "West Coast"}}

&nbsp; <a href="{{cta\_url}}" class="btn">Order before Wednesday for fresh delivery this weekend</a>

{{/eq}}



{{#eq shipping\_zone "East Coast"}}

&nbsp; <a href="{{cta\_url}}" class="btn">You still have 2 days left to grab fresh packs for {{pet\_name}}</a>

{{/eq}}



<!-- Dynamic Image: Breed-specific -->

<img src="{{breed\_image\_url}}" alt="{{pet\_breed}}" style="max-width:100%; height:auto;">



