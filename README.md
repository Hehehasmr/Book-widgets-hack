here is the script



(async function() {
  // Fetch predefined answers (customize this URL or fetch method as needed)
  const answers = [
    "Answer 1",
    "Answer 2",
    "Answer 3",
    "Final Answer"
  ];

  // Select all input fields (text inputs, textareas, and dropdowns)
  const inputFields = document.querySelectorAll('input[type="text"], textarea, select');

  if (inputFields.length === 0) {
    console.warn("No input fields found. Please check the page structure or selectors.");
    return;
  }

  // Fill in the answers
  inputFields.forEach((field, index) => {
    if (answers[index]) {
      if (field.tagName === 'SELECT') {
        field.value = [...field.options].find(opt => opt.text === answers[index])?.value || '';
      } else {
        field.value = answers[index];
      }
      field.dispatchEvent(new Event('input', { bubbles: true }));
    }
  });

  console.log("✅ All answers filled successfully!");
})();
