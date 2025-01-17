# Troubleshooting

Sometimes things go wrong. Here is a list of resolutions to some of the problems you may be experiencing.

## Index

- [I'm not able to connect my application to the playground](#im-not-able-to-connect-my-application-to-the-playground)
- [Some user attributes remain null even after applying a patch](#some-user-attributes-remain-null-after-applying-a-patch)

## I'm not able to connect my application to the playground

These are the most common problems involving playground connectivity:

### Application ID Mismatch

Double-check if the API key you are using to access the playground applies to the application specified in the SDK initialization.

If you are using a URL to access the playground, make sure you are initializing the SDK with sandbox application ID 
`00000000-0000-0000-0000-000000000000`.

### URL Redirection

The playground uses a query-string parameter to initiate the connection to an application. Check if the 
`__cplay` parameter is present in the URL of the application opened from the playground. If not, your server may be 
redirecting the request, which prevents establishing a connection with your application.

## Some user attributes remain null after applying a patch

If you are applying a patch and the attributes are still null, you may be experiencing one of the following problems:

### Invalid Patch

If any operations included in your patch fail, the whole patch fails, and you will not see the changes you are expecting.

Check out the User API and Session API documentation to ensure your patch conforms with the respective attributes' constraints.

### Personally Identified Information (PII)

If you are trying to access personally identifiable information for an anonymous user, the result will be null until 
the user gets identified.

In an effort to protect users’ privacy, Croct does not allow you to access personally identifiable information about 
anonymous users as there is no way for anonymous users to invoke their right to be forgotten.

You can temporarily collect information to let the session unification process automatically migrate them to an 
identified profile when the user signs up. If the user does not signs up, the personalization engine will anonymize 
the profile after the session has expired.


