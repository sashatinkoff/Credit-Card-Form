# Credit-Card-Form
Simple credit card to validate and format card number, expired date and cvs according to determined credit card

Have no idea how to validate and format credit card in your form? This small package may help you. Take a look on MainActivity.kt to get a sample code how you may use it. If you want to have more information about it, follow to the link to the post on Medium (attention, it's written on Russian) https://bit.ly/2LT586O

<pre>
 val creditCards = CreditCardForm(creditCardInput)
                .defaults()
                .cvsInput(cvsInput)
                .expiresInput(expiresInput)
                .focusChains(creditCardInput, expiresInput, cvsInput, btnRead)
                .onCardType { type -> textview.text = "$type" }
                .onFormComplete { btnCar.isEnabled = it }
                .create()
</pre>

To extend a list of types of credit cards, you may use following snippet
<pre>
val cardType = CardType() // Create the new card type
                .name(AMEX) // Set the unique (!!!) name
                .cvsLength(4) // Set the length of CVS 
                .pattern("^3[47][0-9]{2}$") // The unique pattern to determine a card type
                .addRule(4, 6, 5) // A formatting rule
                
creditCards.appendCard(cardType)
</pre>

A card contains the formatting rule. For example, Visa has a following rule: XXXX XXXX XXXX XXXX, American Express - XXXX XXXXXX XXXXX, etc.
So, for Visa we use following rule: <code>addRule(4, 4, 4, 4)</code>, for Amex - <code>addRule(4, 6, 5)</code>

You can get the list of default card types here:
<pre>
        const val AMEX = "American Express"
        const val VISA = "Visa"
        const val MASTER_CARD = "Master Card"
        const val DISCOVER = "Discover"
        const val DINERS_CLUB = "Diners club"
</pre>

A quick video presentation: https://gfycat.com/ru/potabledeafeningbirdofparadise
