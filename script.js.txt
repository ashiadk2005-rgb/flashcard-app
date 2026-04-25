let flashcards = [
  { question: "What is HTML?", answer: "HyperText Markup Language" },
  { question: "What is CSS?", answer: "Cascading Style Sheets" },
  { question: "What is JavaScript?", answer: "Programming language for web" }
];

let index = 0;

// Load card safely
function loadCard() {
  if (flashcards.length === 0) {
    document.getElementById("question").innerText = "No flashcards available";
    document.getElementById("answer").innerText = "";
    return;
  }

  document.getElementById("question").innerText = flashcards[index].question;
  document.getElementById("answer").innerText = flashcards[index].answer;
  document.getElementById("answer").style.display = "none";
}

// Show answer
function showAnswer() {
  document.getElementById("answer").style.display = "block";
}

// Next card
function nextCard() {
  if (flashcards.length === 0) return;
  index = (index + 1) % flashcards.length;
  loadCard();
}

// Previous card
function prevCard() {
  if (flashcards.length === 0) return;
  index = (index - 1 + flashcards.length) % flashcards.length;
  loadCard();
}

// Add card
function addCard() {
  let q = prompt("Enter Question:");
  let a = prompt("Enter Answer:");

  if (q && a) {
    flashcards.push({ question: q, answer: a });
    alert("Card Added!");
    loadCard();
  }
}

// Delete card (FIXED + REQUIRED)
function deleteCard() {
  if (flashcards.length === 0) return;

  let confirmDelete = confirm("Are you sure you want to delete this card?");

  if (confirmDelete) {
    flashcards.splice(index, 1);

    if (index >= flashcards.length) {
      index = 0;
    }

    loadCard();
  }
}

// Initial load
loadCard();