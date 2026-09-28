# IT 140 Module Four Assignment
# Higher/Lower Game Pseudocode Template
#
# Complete the TODO prompts below with your own pseudocode.
# Keep this file in .pseudo format for submission.
#
# Use clear indentation to show decisions and repeated behavior.
# Your finished pseudocode should address every requirement in the
# current Module Four Assignment Guidelines and Rubric.

START hilow_game

    # Establish a valid guessing range.
    SET is_valid_bounds TO FALSE
    WHILE is_valid_bounds IS FALSE DO
        OUTPUT "Enter the lower bound number: "
        INPUT lower_bound
        OUTPUT "Enter the upper bound number: "
        INPUT upper_bound
        
        IF lower_bound IS LESS THAN upper_bound THEN
            SET is_valid_bounds TO TRUE
        ELSE
            OUTPUT "Error: The lower bound must be less than the upper bound. Please try again."
        END IF
    END WHILE

    # Establish the number the player is trying to guess.
    GENERATE a random integer between lower_bound and upper_bound
    SET secret_number TO generated random integer
    SET is_correct_guess TO FALSE
    OUTPUT "Game initialized! I am thinking of a number between " + lower_bound + " and " + upper_bound + "."

    # Play the game.
    SET is_valid_guess TO FALSE
    WHILE is_valid_guess IS FALSE DO
        OUTPUT "Enter your guess (between " + lower_bound + " and " + upper_bound + "): "
        INPUT user_guess
        
        IF user_guess IS GREATER THAN OR EQUAL TO lower_bound AND user_guess IS LESS THAN OR EQUAL TO upper_bound THEN
            SET is_valid_guess TO TRUE
        ELSE
            OUTPUT "Error: Out of bounds! Your guess must be between " + lower_bound + " and " + upper_bound + "."
        END IF
    END WHILE

    WHILE is_correct_guess IS FALSE DO
        IF user_guess IS EQUAL TO secret_number THEN
            OUTPUT "Congratulations! You got it! That is the right number!"
            SET is_correct_guess TO TRUE
        ELSE IF user_guess IS LESS THAN secret_number THEN
            OUTPUT "Too low! Try a higher number."
        ELSE IF user_guess IS GREATER THAN secret_number THEN
            OUTPUT "Too high! Try a lower number."
        END IF

        IF is_correct_guess IS FALSE THEN
            SET is_valid_guess TO FALSE
            WHILE is_valid_guess IS FALSE DO
                OUTPUT "Enter another guess (between " + lower_bound + " and " + upper_bound + "): "
                INPUT user_guess
                
                IF user_guess IS GREATER THAN OR EQUAL TO lower_bound AND user_guess IS LESS THAN OR EQUAL TO upper_bound THEN
                    SET is_valid_guess TO TRUE
                ELSE
                    OUTPUT "Error: Out of bounds! Your guess must be between " + lower_bound + " and " + upper_bound + "."
                END IF
            END WHILE
        END IF
    END WHILE

    OUTPUT "Thank you for playing the Higher/Lower game!"

END hilow_game
