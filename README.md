### Hi there, I'm Kami! 👋


[Linkedin](https://www.linkedin.com/in/camila-moreno-ricca/) ◆ [Trailblazer](https://trailblazer.me/id/cmorenoricca) ◆ [Gmail](mailto:morenoricca.camila@gmail.com?subject=Hello%20Kami,%20From%20Github")

```js
import { LightningElement, wire } from 'lwc';
import getKamila from '@salesforce/apex/Wrapper.getKamila';
import KMC from '@salesforce/messageChannel/KamiMessageChannel__c';

export default class KamiInfo extends LightningElement {

    @wire(MessageContext)
    messageContext;
    KamiBio;
    KamiDeveloper;
    KamiContactInfo;
    
    @wire(getKamila)
    wiredDeveloper(data, error){

        if(data){
        
          this.HandleSuccesfulLoad();
          
          this.KamiBio = {
                          name: 'Camila Moreno Ricca',
                          age: undefined,
                          currentLocation: 'Buenos Aires, Argentina'
                          };
        
          this.KamiDeveloper = {
                                title: 'Salesforce Developer',
                                skills: ['HTML', 'CSS', 'JavaScript', 'Bootstrap', 'LWC', 
                                          'APEX', 'SOQL', 'GIT', 'GitHub', 'Trello'],
                                company: null
                               };
                                
          this.handleContactInfo();
        
        }else if(error){
        
          console.log(error);
        }
        
        handleContactInfo(){
        
            this.KamiContactInfo.forEach(()=>{
            
                console.log(contactInfo);
            })
        }
        
        handleSuccessfulLoad() {

          const messagePayload = {

              'Thank you for reading!'
          };

          publish(this.messageContext, KMC, {
              payload: messagePayload
          });

       }

}
```
