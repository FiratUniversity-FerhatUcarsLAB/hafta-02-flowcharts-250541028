AD SOYAD : NUH DAĞ
ÖĞRENCİ NUMARASI:250541028

BEGIN

    INSERT card
    PROMPT "Please enter your PIN:"
    SET pin_attempts = 0

    WHILE pin_attempts < 3 DO
        READ entered_pin
        IF entered_pin == correct_pin THEN
            BREAK
        ELSE
            pin_attempts = pin_attempts + 1
            DISPLAY "Incorrect PIN!"
            IF pin_attempts == 3 THEN
                DISPLAY "Card blocked. Contact your bank."
                TERMINATE
            ENDIF
        ENDIF
    ENDWHILE

    REPEAT
        DISPLAY "1. Check Balance"
        DISPLAY "2. Withdraw Money"
        DISPLAY "3. Exit"
        PROMPT "Select an option:"
        READ choice

        IF choice == 1 THEN
            DISPLAY "Your balance is: ", balance

        ELSE IF choice == 2 THEN
            PROMPT "Enter amount to withdraw:"
            READ amount

            IF amount > balance THEN
                DISPLAY "Insufficient balance."
            
            ELSE IF amount MOD 20 != 0 THEN
                DISPLAY "Amount must be a multiple of 20 TL."

            ELSE IF amount > daily_limit THEN
                DISPLAY "Daily limit exceeded."

            ELSE
                balance = balance - amount
                DISPLAY "Please take your cash."
                DISPLAY "Printing receipt..."
            ENDIF

        ELSE IF choice == 3 THEN
            DISPLAY "Thank you for using our ATM."
            EJECT card
            TERMINATE

        ELSE
            DISPLAY "Invalid selection."
        ENDIF

        PROMPT "Would you like to perform another transaction? (Y/N)"
        READ answer
    UNTIL answer == 'N' OR answer == 'n'

    EJECT card
    DISPLAY "Have a nice day!"
    TERMINATE

END
