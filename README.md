<!DOCTYPE html>
<html>
    <head>

        <meta charset="utf-8">
        <title>bank deposit example</title>
        <script>
            var user = {
                userName: 'Ernesto',
                password: 'AmeliaQuintana',
                current_bill: 100,
                payment_history: [
                    45, 55, 65
                ],
                messageToUser : function(){
                    alert('No amount entered!');
                },
                payBill: function(){

                    if(this.current_bill > 0){
                        var amountPaid = prompt(`Current bill is ${this.current_bill}. How much would you like to pay? `)
                    }else {
                        alert('No bill!')
                        return;
                    }
                    amountPaid = parseInt(amountPaid)// use parseInt() to make sure amountPaid is a number and not a string
                    if (!amountPaid) {
                        this.messageToUser('error') // <~~~~ use this.messageToUser() instead
                        this.payBill() // restart the process
                        return; // STOP
                    }
                    if (amountPaid > this.current_bill) {
                        alert(`Error!Amount exceeds current bill of $${this.current_bill}`)
                        this.payBill()
                        return;
                    }else {
                    this.payment_history.push(amountPaid);
                    this.current_bill = (this.current_bill - amountPaid)
                }
                alert(`Thank you for your payment of ${amountPaid}$`)

                var anotherPayment = confirm('Would you like to make another payment at this time?')
                if ( anotherPayment == true) {
                    this.payBill()
                    return;

                }else {
                    alert('Thank you for your payment')
                }
                },


                login: function(){
                    var userName = prompt('What is your User Name?')


                    var password = prompt('What is your password?')
                    if (password != this.password || userName != this.userName) {
                        alert('Incorrect User Name or Password combination!')
                        this.login()
                        return;
                    }else {
                        this.payBill()
                        return;
                    }
                }

            }

            user.login()
            user.payBill()




        </script>







    </head>
    <body>

    </body>
</html>
