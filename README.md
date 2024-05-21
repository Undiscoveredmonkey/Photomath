Yeah copy this 
// Function to scan the webpage for math problems and provide answers
function scanForMathProblems() {
    // Regular expression to match mathematical expressions (e.g., "2 + 2" or "3 * 5")
    var mathRegex = /[0-9]+(\s*[\+\-\*\/]\s*[0-9]+)+/g;

    // Get the text content of the entire webpage
    var pageContent = document.body.innerText;

    // Find all math expressions in the page content
    var mathExpressions = pageContent.match(mathRegex);

    // If there are math expressions found
    if (mathExpressions && mathExpressions.length > 0) {
        // Loop through each math expression
        for (var i = 0; i < mathExpressions.length; i++) {
            var mathExpression = mathExpressions[i];

            // Evaluate the math expression to get the answer
            var answer;
            try {
                answer = eval(mathExpression); // Using eval is not recommended for security reasons, consider using a safe alternative
            } catch (error) {
                console.error("Error evaluating expression:", error);
                continue;
            }

            // Display the math expression and its answer to the user
            console.log("Math Problem:", mathExpression, "Answer:", answer);
        }
    } else {
        console.log("No math problems found on this page.");
    }
}

// Call the function when the webpage has finished loading
window.onload = scanForMathProblems;
