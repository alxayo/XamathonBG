# XamathonBG #
Some code artifacts part of the Xamarin Hackathon 2016 in Sofia, Bulgaria
details about the event could be foudn here: https://www.microsoft.com/bg-bg/xamathon/program.aspx

## XamathonBG ##

As part of the Xamarin Hackathon 2016 Sofia the tems have woerked on multiple projects. 
One of the project used kick start the development was __Displaying Pop-up__

* Guide is avaliable here: https://developer.xamarin.com/guides/xamarin-forms/application-fundamentals/navigation/pop-ups/
* Source on gitHub: https://github.com/xamarin/xamarin-forms-samples/tree/master/Navigation/Pop-ups/WorkingWithPopups

The teams used it to set-up their development environements and do some tests. 

The project was build and tested on Windows and Android devices, as well as on iOS simulator trough Mac build agent.
![Xamarin app on Winodws device and iOS simulator](https://github.com/xayo/XamathonBG/blob/master/screenshots/XamarinDevelopment.jpg)


An interesting experiment was build on top of this application where one could integrate the Xamarin application with Azure Logic App.
Details about Azure Logic Apps: https://azure.microsoft.com/en-us/services/logic-apps/

The resulting solution had the following functionaity:
Azure Logic App that is connected to a Twitter acount and accepts input.
Details about Logic app and twitter here: https://docs.microsoft.com/en-us/azure/connectors/connectors-create-api-twitter

The "Displaying Pop-up" Xamarin application was modiifed so that it accepts user input and calls HTTP logic app triger to post the supplied text in twitter. 

The Xamarin application do not hold any user credentials for the Twitter account. the http call is asynchronous and does not block the mobile application. 

The application was tested on Winodws device, Andoird Device and iOS simulator. Series of twitter post were recoreded durin the tests: 

![Xamarin and Azure Logic App tests with twitter](https://github.com/xayo/XamathonBG/blob/master/screenshots/XamarinLogicAppsTwitterTests.PNG)


## Code ##

Only 2 file form the original sample were modified in order to implement this solution. the files are abaliable under the **/src** folder.

The essential part is 3 lines of code part of [AlertPage.xaml](https://github.com/xayo/XamathonBG/blob/master/src/AlertPage.xaml) :
``` //Http Request
var httpClient = new HttpClient();
var content = new StringContent(this.twiterbody.Text);
var result = await httpClient.PostAsync(connectURL, content).ConfigureAwait(false);
```