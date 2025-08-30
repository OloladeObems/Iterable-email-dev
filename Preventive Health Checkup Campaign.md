**Preventive Health Checkup Campaign – Dynamic Personalization Template**



**Purpose:**

Advanced personalization for health plan members based on:



1. Plan type (Corporate, Retail, Family, Premium)
2. Claims history (dental, maternity, lab tests, last claim date)
3. Demographics (age, gender, marital status, location)
4. Engagement score (opens/clicks in last 90 days)
5. Location-specific recommendations (Nigeria, UAE, Egypt)



**Output:**

This single template dynamically renders:

1. Header
2. Personalized body copy
3. CTA (simplified for low engagement users)
4. Conditional footers





###### ***Handlebars Code***



{{!-- 

===============================================================

TEMPLATE: Preventive Health Checkup Campaign

PURPOSE:  Advanced personalisation for health plan members based on plan type, claims history, demographics,engagement score, and location.

OUTPUT:   Dynamically renders header, body, CTA, and footer specific to each recipient in a single template.

===============================================================

--}}




<!-- Header -->

<h1>Hi {{first\_name}}, it’s time to put your {{plan\_type}} benefits to work.</h1>



<!-- Dynamic Body Copy -->

{{!-- Age-based recommendation --}}

{{#if (gt age 45)}}

 <p>As you’re over 45, your plan covers a <strong>free heart screening test</strong>. Don’t miss this important check.</p>

{{/if}}



{{!-- Retail plan with no claims in 12 months --}}

{{#if (and (eq plan\_type "Retail") (gt (diff (now) last\_claim\_date "months") 12))}}

 <p>Don’t leave your benefits unused – book your <strong>free annual checkup</strong> today.</p>

{{/if}}



{{!-- Corporate plan + spouse enrolled --}}

{{#if (and (eq plan\_type "Corporate") spouse\_enrolled)}}

<p>Your plan also covers <strong>family screening packages</strong>. Take care of your loved ones, too.</p>

{{/if}}



{{!-- Engagement-based simplification --}}

{{#if (lt engagement\_score 30)}}

 <p>Take charge of your health today.</p>

 <a href="{{call\_to\_action\_url}}" class="btn">Book Your Checkup</a>

{{else}}

<p>Explore the full range of screenings your plan covers. Choose what works best for you.</p>

 <a href="{{call\_to\_action\_url}}" class="btn">See My Benefits</a>

{{/if}}



<!-- Conditional Footer -->

<hr>

{{#eq location "Nigeria"}}

 <p><strong>Our Partner Hospitals in Nigeria:</strong> Lagos General, Abuja Clinic, Ibadan MedCare.</p>

{{/eq}}



{{#eq location "UAE"}}

<p><strong>Teleconsultation Options in UAE:</strong> Book a virtual session with our certified doctors.</p>

{{/eq}}



{{#eq location "Egypt"}}

 <p><strong>Partner Hospitals in Egypt:</strong> Cairo MedCenter, Alexandria Health.</p>

<p><strong>Teleconsultation Options:</strong> Access remote specialists anytime.</p>

{{/eq}}




