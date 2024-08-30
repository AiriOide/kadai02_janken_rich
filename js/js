document.addEventListener('DOMContentLoaded', function() {
    const questions = [
        {
            question: "あなたの主な投資目標は何ですか？",
            options: [
                "資本の保全",
                "安定した収入の生成",
                "長期的な成長の達成",
                "短期的な利益の最大化"
            ]
        },
        {
            question: "投資が1年で20%損失した場合、どう反応しますか？",
            options: [
                "すぐにすべて売却する",
                "一部の投資を売却する",
                "保有し続け、回復を待つ",
                "さらに買い増しする"
            ]
        },
        {
            question: "あなたの投資期間はどのくらいですか？",
            options: [
                "1年未満",
                "1-3年",
                "3-10年",
                "10年以上"
            ]
        }
    ];

    let currentQuestion = 0;
    let score = 0;

    const introContainer = document.getElementById('intro-container');
    const questionContainer = document.getElementById('question-container');
    const resultContainer = document.getElementById('result-container');
    const startButton = document.getElementById('start-btn');
    const nextButton = document.getElementById('next-btn');
    const submitButton = document.getElementById('submit-btn');
    const restartButton = document.getElementById('restart-btn');

    startButton.addEventListener('click', startQuiz);
    nextButton.addEventListener('click', nextQuestion);
    submitButton.addEventListener('click', showResult);
    restartButton.addEventListener('click', restartQuiz);

    function startQuiz() {
        introContainer.style.display = 'none';
        questionContainer.style.display = 'block';
        displayQuestion();
    }

    function displayQuestion() {
        const question = questions[currentQuestion];
        let html = `<div class="question">
                        <h2>質問 ${currentQuestion + 1} / ${questions.length}</h2>
                        <p>${question.question}</p>
                        <div class="options">`;
        
        question.options.forEach((option, index) => {
            html += `<label class="option">
                        <input type="radio" name="answer" value="${index}">
                        ${option}
                     </label>`;
        });
        
        html += '</div></div>';
        questionContainer.innerHTML = html;

        nextButton.style.display = 'block';
        submitButton.style.display = 'none';
        
        if (currentQuestion === questions.length - 1) {
            nextButton.style.display = 'none';
            submitButton.style.display = 'block';
        }
    }

    function nextQuestion() {
        const selectedOption = document.querySelector('input[name="answer"]:checked');
        if (selectedOption) {
            score += parseInt(selectedOption.value) + 1;
            currentQuestion++;
            if (currentQuestion < questions.length) {
                displayQuestion();
            } else {
                showResult();
            }
        } else {
            alert('回答を選択してから次へ進んでください。');
        }
    }

    function getInvestmentType(score) {
        if (score <= 4) return "保守的";
        if (score <= 7) return "やや保守的";
        if (score <= 10) return "バランス型";
        if (score <= 13) return "成長志向";
        return "積極的成長";
    }

    function showResult() {
        questionContainer.style.display = 'none';
        resultContainer.style.display = 'block';
        
        const investmentType = getInvestmentType(score);
        resultContainer.innerHTML = `
            <h2>あなたの投資タイプ</h2>
            <img src="/api/placeholder/200/200" alt="${investmentType}" class="result-image">
            <p><strong>${investmentType}</strong></p>
            <p>スコア: ${score} / ${questions.length * 4}</p>
        `;
    }

    function restartQuiz() {
        currentQuestion = 0;
        score = 0;
        resultContainer.style.display = 'none';
        introContainer.style.display = 'block';
    }
});
