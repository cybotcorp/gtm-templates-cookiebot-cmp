# Cookiebot CMP template for Google Tag Manager
With this template you can use the cookie consent provider Cookiebot in Google Tag Manager to obtain cookie consent from website users and control GTM tags that are setting cookies in accordance with the user's consent.

Please follow these guidelines for implementation:

1. Create an account on https://www.cookiebot.com and add the domain name of your website. Copy out the "Cookiebot ID" from the domain group you have registered the domain under (tab 'Your Scripts').

2. In GTM, add the "Cookiebot CMP" tag and save the Cookie ID into the corresponding field.

3. Add the GTM variable template "Cookiebot Consent State" (https://github.com/cybotcorp/gtm-templates-cookiebot-variable) to your GTM configuration and name it "Cookie Consent".

4. Add the following triggers to your GTM configuration:
- Event Name: cookie_consent_preferences, Event Type: Custom Event, Fires On: Some Custom Events, Filter: Cookie Consent - contains - preferences
- Event Name: cookie_consent_statistics, Event Type: Custom Event, Fires On: Some Custom Events, Filter: Cookie Consent - contains - statistics
- Event Name: cookie_consent_marketing, Event Type: Custom Event, Fires On: Some Custom Events, Filter: Cookie Consent - contains - marketing

5. Tags that are setting cookies within one of the three categories (see scan report from Cookiebot if you are in doubt) must only be triggered when the user has consented to the relevant category/categories. For this, replace the existing Firing Trigger on each cookie-setting tag with the relevant cookie-trigger, e.g. "cookie_consent_statistics" for Analytics. If a tag requieres more than one trigger, e.g. multiple cookie-categories, create a new trigger of type "Trigger Group" and add all the relevant cookie-triggers and any other trigger and set "This trigger fires on" to "All conditions" and replace the tag's existing trigger with this Trigger Group. This ensures that tags that are setting cookies only fire when the user has consented to the type of cookies being used by the tag.

To make available an option for the user to change or withdraw consent, implement Cookiebot's 'Cookie Declaration' on a page of your own choice as described under the last step in Cookiebot's general implementation guide: https://www.cookiebot.com/goto/help. Make sure to link to the page that embeds the declaration from all pages on your website, e.g. in the website template footer.
