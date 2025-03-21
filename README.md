public class PizzaDiscountScheduler implements Schedulable {
    public void execute(SchedulableContext sc) {
        // Logic for sending the email
        
        // Check if today is Sunday
        if (DateTime.now().format('E') == 'Sun') {
            List<Customer_Detail__c> pz = new List<Customer_Detail__c>();
            String s = 'gmail.com';
            
            for (Customer_Detail__c c : pz) {
                if (c.Email__c != null && c.Email__c.contains(s)) {
                    System.debug('haiiiii');
                }
            }
            
            // Sending the email
            Messaging.SingleEmailMessage email = new Messaging.SingleEmailMessage();
            email.setToAddresses(new List<String>{'user@example.com'});
            email.setSubject('Special Sunday Discount');
            email.setPlainTextBody('Enjoy a 20% discount on all pizzas today!');
            Messaging.sendEmail(new List<Messaging.SingleEmailMessage>{email});
        }
    }
}
