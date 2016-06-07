Regarding text selection; I’ve done some tests in the past to avoid the cut/copy/paste menu and I was able to disable it with some CSS:

<style>
input {
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
}
</style>
 
Or even to the text:
 
<style>
.unselectable {
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
}
</style>
 
<div class="unselectable">
<h1>Test</h1>
</div>

To bee able to select phone numbers and activate directly the phone application, again, some HTML and JavaScript may be able to achieve what you’re looking for, in particular something linked to the "phone:” URI:
http://rickluna.com/wp/2012/02/making-a-phone-call-from-within-phonegap-in-android-and-ios/

If you need the auto link feature:


<uses-permission
android:autoLink="phone"
/>

We probably need to ask to add this to EB runtime…
