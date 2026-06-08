<!DOCTYPE html>
<html lang="hy">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English 2003 - Շտեմարանի Պատասխաններ</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        body {
            background-color: #f4f6f9;
            color: #333;
            padding: 20px;
        }
        header {
            text-align: center;
            background: linear-gradient(135deg, #2c3e50, #3498db);
            color: white;
            padding: 30px;
            border-radius: 10px;
            margin-bottom: 25px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        header h1 {
            font-size: 24px;
            margin-bottom: 5px;
        }
        header p {
            font-size: 14px;
            opacity: 0.9;
        }
        .tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
            gap: 10px;
        }
        .tab-btn {
            padding: 12px 24px;
            font-size: 16px;
            font-weight: bold;
            border: none;
            background-color: #e0e0e0;
            color: #555;
            cursor: pointer;
            border-radius: 5px;
            transition: all 0.3s ease;
        }
        .tab-btn.active {
            background-color: #3498db;
            color: white;
            box-shadow: 0 4px 6px rgba(52, 152, 219, 0.3);
        }
        .tab-content {
            display: none;
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            max-width: 800px;
            margin: 0 auto;
        }
        .tab-content.active {
            display: block;
        }
        .exercise-item {
            border-bottom: 1px solid #eee;
            padding: 15px 0;
        }
        .exercise-item:last-child {
            border-bottom: none;
        }
        .num {
            font-weight: bold;
            color: #3498db;
            margin-right: 5px;
        }
        .active-text {
            font-weight: 500;
            color: #2c3e50;
            margin-bottom: 5px;
        }
        .passive-text {
            font-style: italic;
            color: #27ae60;
            padding-left: 15px;
            border-left: 3px solid #27ae60;
        }
        .placeholder-text {
            color: #7f8c8d;
            font-style: italic;
            text-align: center;
            padding: 20px;
        }
    </style>
</head>
<body>

<header>
    <h1>Անգլերեն 2003 Շտեմարան</h1>
    <p>Վարժությունների Պատասխանների Հավաքածու</p>
</header>

<div class="tabs">
    <button class="tab-btn active" onclick="openTab(event, 'passive')">Passive Voice</button>
    <button class="tab-btn" onclick="openTab(event, 'reported')">Reported Speech</button>
    <button class="tab-btn" onclick="openTab(event, 'questions')">Questions</button>
</div>

<!-- PASSIVE VOICE SECTION -->
<div id="passive" class="tab-content active">
    <h2>Passive Voice (Համարներ 82-149)</h2>
    <div id="passive-list"></div>
</div>

<!-- REPORTED SPEECH SECTION -->
<div id="reported" class="tab-content">
    <h2>Reported Speech</h2>
    <p class="placeholder-text">Այս բաժնի պատասխանները կարող ես ավելացնել կոդի մեջ (reportedData մասում)։</p>
</div>

<!-- QUESTIONS SECTION -->
<div id="questions" class="tab-content">
    <h2>Questions (Հարցեր)</h2>
    <p class="placeholder-text">Այս բաժնի պատասխանները կարող ես ավելացնել կոդի մեջ (questionsData մասում)։</p>
</div>

<script>
    // Passive Voice տվյալները (նկարի հիման վրա)
    const passiveData = [
        { num: 82, act: "How often do you paint your room?", pas: "How often is your room painted?" },
        { num: 83, act: "She said that they had never spoken to her in such a way.", pas: "She said that she had never been spoken to in such a way." },
        { num: 84, act: "Have all of you copied the text?", pas: "Has the text been copied by all of you?" },
        { num: 85, act: "I usually write a letter to my friend in the evening.", pas: "A letter is usually written to my friend in the evening." },
        { num: 86, act: "How many English books have you read?", pas: "How many English books have been read by you?" },
        { num: 87, act: "How many lessons have you done?", pas: "How many lessons have been done by you?" },
        { num: 88, act: "What exhibition halls do they include in the guide books?", pas: "What exhibition halls are included in the guide books?" },
        { num: 89, act: "The waitress brought me a cup of tea.", pas: "A cup of tea was brought to me by the waitress. / I was brought a cup of tea by the waitress." },
        { num: 90, act: "I think you must solve this problem as soon as possible.", pas: "I think this problem must be solved as soon as possible." },
        { num: 91, act: "Which lessons are you doing now?", pas: "Which lessons are being done by you now?" },
        { num: 92, act: "Usually he buys his clothes in this shop.", pas: "Usually his clothes are bought in this shop." },
        { num: 93, act: "I am planning my free time.", pas: "My free time is being planned by me." },
        { num: 94, act: "I am sure you'll find his new address in the Inquiry Book.", pas: "I am sure his new address will be found in the Inquiry Book." },
        { num: 95, act: "What did you cook for supper?", pas: "What was cooked for supper?" },
        { num: 96, act: "We translate this kind of texts at every lesson.", pas: "This kind of texts is translated at every lesson." },
        { num: 97, act: "They took him to the doctor.", pas: "He was taken to the doctor." },
        { num: 98, act: "We hear a sound of a violin in the hall.", pas: "A sound of a violin is heard in the hall." },
        { num: 99, act: "His father always praises him when he works hard.", pas: "He is always praised by his father when he works hard." },
        { num: 100, act: "They have offered him an interesting job.", pas: "An interesting job has been offered to him. / He has been offered an interesting job." },
        { num: 101, act: "What kind of exercises do you usually do in class?", pas: "What kind of exercises are usually done in class?" },
        { num: 102, act: "We always listen to our lecturer attentively.", pas: "Our lecturer is always listened to attentively." },
        { num: 103, act: "They looked at the picture with admiration.", pas: "The picture was looked at with admiration." },
        { num: 104, act: "They play football all over the world.", pas: "Football is played all over the world." },
        { num: 105, act: "Somebody must look after the children when we are away.", pas: "The children must be looked after when we are away." },
        { num: 106, act: "They were discussing this problem at the lecture.", pas: "This problem was being discussed at the lecture." },
        { num: 107, act: "They speak much about the book.", pas: "The book is much spoken about." },
        { num: 108, act: "They found the envelope on the shelf.", pas: "The envelope was found on the shelf." },
        { num: 109, act: "He bought this book a week ago.", pas: "This book was bought a week ago." },
        { num: 110, act: "I thought that she had already received the letter.", pas: "I thought that the letter had already been received by her." },
        { num: 111, act: "He often writes his letters in haste.", pas: "His letters are often written in haste." },
        { num: 112, act: "John broke the window when playing football in the yard.", pas: "The window was broken by John when playing football in the yard." },
        { num: 113, act: "He will post that letter tomorrow.", pas: "That letter will be posted tomorrow." },
        { num: 114, act: "They are discussing your report now.", pas: "Your report is being discussed now." },
        { num: 115, act: "We shall change our time-table in a week.", pas: "Our time-table will be changed in a week." },
        { num: 116, act: "Tom met them yesterday.", pas: "They were met by Tom yesterday." },
        { num: 117, act: "The secretary has just brought this letter.", pas: "This letter has just been brought by the secretary." },
        { num: 118, act: "Why haven't they sent the letter yet?", pas: "Why hasn't the letter been sent yet?" },
        { num: 119, act: "They showed her the shortest way to the station.", pas: "The shortest way to the station was shown to her. / She was shown the shortest way to the station." },
        { num: 120, act: "We asked the lecturer a few questions about Shakespeare.", pas: "A few questions about Shakespeare were asked to the lecturer. / The lecturer was asked a few questions about Shakespeare." },
        { num: 121, act: "Tom has just told us an interesting story.", pas: "An interesting story has just been told to us by Tom. / We have just been told an interesting story by Tom." },
        { num: 122, act: "His friends gave him a good piece of advice.", pas: "A good piece of advice was given to him by his friends. / He was given a good piece of advice by his friends." },
        { num: 123, act: "He said they had asked him twice about it.", pas: "He said he had been asked twice about it." },
        { num: 124, act: "I sent her brother a telegram.", pas: "A telegram was sent to her brother. / Her brother was sent a telegram." },
        { num: 125, act: "They'll explain the rule to him.", pas: "The rule will be explained to him." },
        { num: 126, act: "They had to operate on my brother.", pas: "My brother had to be operated on." },
        { num: 127, act: "We often see him at the exhibitions.", pas: "He is often seen at the exhibitions." },
        { num: 128, act: "They agreed upon the plan.", pas: "The plan was agreed upon." },
        { num: 129, act: "I'm giving a party this week.", pas: "A party is being given this week." },
        { num: 130, act: "The boys have broken the girl's doll.", pas: "The girl's doll has been broken by the boys." },
        { num: 131, act: "They took no notice of his words.", pas: "No notice was taken of his words. / His words were taken no notice of." },
        { num: 132, act: "We can't hear her voice from here.", pas: "Her voice can't be heard from here." },
        { num: 133, act: "His friends always laugh at him.", pas: "He is always laughed at by his friends." },
        { num: 134, act: "By the time the director came she had typed the letters.", pas: "By the time the director came the letters had been typed by her." },
        { num: 135, act: "They worked out the project last week.", pas: "The project was worked out last week." },
        { num: 136, act: "They will sponsor the tree planting project.", pas: "The tree planting project will be sponsored by them." },
        { num: 137, act: "Did your brother break the window?", pas: "Was the window broken by your brother?" },
        { num: 138, act: "We have corrected all the mistakes.", pas: "All the mistakes have been corrected." },
        { num: 139, act: "Where do they sell books in foreign languages?", pas: "Where are books in foreign languages sold?" },
        { num: 140, act: "He locked the front door of the house.", pas: "The front door of the house was locked." },
        { num: 141, act: "Everybody must obey the instructions.", pas: "The instructions must be obeyed by everybody." },
        { num: 142, act: "When did they buy the tickets?", pas: "When were the tickets bought?" },
        { num: 143, act: "Finally they persuaded him to agree.", pas: "Finally he was persuaded to agree." },
        { num: 144, act: "They will publish his new book soon.", pas: "His new book will be published soon." },
        { num: 145, act: "Have they sent the invitations yet?", pas: "Have the invitations been sent yet?" },
        { num: 146, act: "You must study the instruction before using the machine.", pas: "The instruction must be studied before using the machine." },
        { num: 147, act: "I lost my wallet yesterday.", pas: "My wallet was lost yesterday." },
        { num: 148, act: "Have you already sent the telegrams?", pas: "Have the telegrams already been sent?" },
        { num: 149, act: "You can find this kind of dictionaries in that shop.", pas: "This kind of dictionaries can be found in that shop." }
    ];

    // Գեներացնում ենք Passive-ի ցուցակը կայքում
    const passiveList = document.getElementById('passive-list');
    passiveData.forEach(item => {
        const div = document.createElement('div');
        div.className = 'exercise-item';
        div.innerHTML = `
            <div class="active-text"><span class="num">${item.num}.</span> ${item.act}</div>
            <div class="passive-text">→ ${item.pas}</div>
        `;
        passiveList.appendChild(div);
    });

    // Տաբերի փոփոխման ֆունկցիա
    function openTab(evt, tabName) {
        const tabcontents = document.getElementsByClassName("tab-content");
        for (let i = 0; i < tabcontents.length; i++) {
            tabcontents[i].classList.remove("active");
        }
        const tabbtns = document.getElementsByClassName("tab-btn");
        for (let i = 0; i < tabbtns.length; i++) {
            tabbtns[i].classList.remove("active");
        }
        document.getElementById(tabName).classList.add("active");
        evt.currentTarget.classList.add("active");
    }
</script>
</body>
</html>
