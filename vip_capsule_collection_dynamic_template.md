**Scenario: Advanced personalization for a “VIP Capsule Collection Launch” campaign.**



Purpose:



Advanced personalization for luxury fashion customers based on:


1. Purchase history (dresses, handbags, shoes)
2. Spend tier (High-spender, Mid-spender, One-time buyer)
3. Color preferences (from wishlist)
4. Event triggers (cart abandonment, wishlist update, past browsing)
5. Loyalty program tier (Gold, Platinum, Elite)



Output:

Single template dynamically renders:

1. Subject line personalization
2. Body copy with product recommendations, limited edition highlights, stylist links
3. Cart abandonment reminders
4. Footer with boutique location and event invitations





**Handlebar code**



{{!-- 

===============================================================

&nbsp; TEMPLATE: VIP Capsule Collection Launch

&nbsp; PURPOSE:  Personalized luxury email experience for capsule collection launch based on purchase history, spend tier, wishlist, event triggers, and loyalty tier.

&nbsp; OUTPUT:   Subject line, body copy, product recommendations, CTA, and footer personalized for each customer.

===============================================================

--}}



<!-- Subject Line -->



{{#if (eq loyalty\_tier "Elite")}}

&nbsp; {{subject\_line = (concat first\_name ", your private capsule invite is here 🖤")}}

{{else if (eq spend\_tier "Mid-spender")}}

&nbsp; {{subject\_line = "The collection you’ve been eyeing is finally here"}}

{{else}}

&nbsp; {{subject\_line = "Discover our VIP Capsule Collection"}}

{{/if}}



<!-- Greeting -->

<h1>Hi {{first\_name}}, welcome to your exclusive capsule experience.</h1>



<!-- Dynamic Body Copy -->



{{!-- Handbag buyer recommendation --}}

{{#if (and (contains last\_purchases "handbag") (lt days\_since\_purchase 90))}}

&nbsp; <p>Complete your look with matching shoes we’ve handpicked for you.</p>

{{/if}}



{{!-- Wishlist color match --}}

{{#if (contains wishlist "emerald green dress")}}

&nbsp; <p>We’ve added a <strong>limited edition emerald green capsule piece</strong> just for you.</p>

{{/if}}



{{!-- High-Spender \& Elite Member --}}

{{#if (and (eq spend\_tier "High-spender") (eq loyalty\_tier "Elite"))}}

&nbsp; <p>Enjoy exclusive access to our <strong>concierge shopping experience</strong> and book a session with your personal stylist.</p>

&nbsp; <a href="{{stylist\_booking\_url}}" class="btn">Book Your Stylist</a>

{{/if}}



{{!-- Cart abandonment dynamic pull --}}

{{#if (lt hours\_since\_cart\_abandonment 48)}}

&nbsp; <p>We noticed you left some items in your cart. Don’t miss out on your favorites:</p>

&nbsp; {{#each abandoned\_cart\_items}}

&nbsp;   <div>

&nbsp;     <img src="{{image\_url}}" alt="{{product\_name}}" style="max-width:100px;">

&nbsp;     <p>{{product\_name}}</p>

&nbsp;   </div>

&nbsp; {{/each}}

&nbsp; <a href="{{cart\_url}}" class="btn">Return to Cart</a>

{{/if}}



<!-- Footer: Boutique + Event -->

<hr>

<p>Visit your nearest boutique:</p>

{{#eq location "Lagos"}}

&nbsp; <p>Lagos Trunk Show – Exclusive Preview Event</p>

{{/eq}}

{{#eq location "London"}}

&nbsp; <p>London Pop-Up – Private Capsule Preview</p>

{{/eq}}



