
<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8" />
  <title>Auto-update Duty Roster (Final Fix with Monday)</title>
  <style>
    body {
      background: #f0f0f0;
      font-family: Arial, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 40px 20px;
      min-height: 100vh;
    }

    h1 {
      text-align: center;
      font-size: 2em;
      margin: 30px 0;
      color: #fff;
      background: linear-gradient(135deg, #764ba2, #ff0003);
      border-radius: 30px;
      padding: 15px 40px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    }
 h2 {
text-align: center;
      font-size: 2em;
      margin: 30px 0;
      color: #fff;
      background: linear-gradient(135deg, #764ba2, #ff0003);
      border-radius: 30px;
      padding: 15px 40px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    }


    .boxes-row {
      display: flex;
      gap: 30px;
      justify-content: center;
      flex-wrap: wrap;
      margin-bottom: 40px;
    }

    .box-group {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .box-heading {
      font-size: 1.1em;
      margin-bottom: 8px;
      color: #fff;
      background: linear-gradient(135deg, #43cea2, #185a9d);
      border-radius: 20px;
      padding: 6px 18px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    .box {
      width: 220px;
      min-height: 140px;
      color: #fff;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      border-radius: 20px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      font-size: 1.1em;
      text-align: center;
      padding: 20px;
      transition: transform 0.3s, box-shadow 0.3s;
    }

    .box:hover {
      transform: translateY(-5px) scale(1.02);
      box-shadow: 0 12px 25px rgba(0,0,0,0.3);
    }

    .box1 { background: linear-gradient(135deg, #667eea, #764ba2); }
    .box2 { background: linear-gradient(135deg, #ff7e5f, #feb47b); }
    .box3 { background: linear-gradient(135deg, #43cea2, #185a9d); }
    .box4 { background: linear-gradient(135deg, #554600,#2e2400); }

    .name { font-size: 1.6em; font-weight: bold; margin-bottom: 10px; }
    .info { font-size: 0.8em; opacity: 0.9; }
    .shift { padding-bottom: 10px; font-weight: bold; }

    @media (max-width: 900px) {
      .boxes-row { flex-direction: column; align-items: center; }
    }
  </style>
</head>
<body>
  
<h1>CHC Itwa Siddharthnagar Staff Nurse Duty Roster</h1>


  <h2>JSY Staff Auto-update Duty Chart</h2>
  <div class="boxes-row">
    <div class="box-group">
      <div class="box-heading">Morning</div>
      <div class="box box1">
        <div class="shift">सुबह ☀️</div>
        <div class="name" id="name1"></div>
        <div class="info" id="info1"></div>
      </div>
    </div>
    <div class="box-group">
      <div class="box-heading">Evening</div>
      <div class="box box2">
        <div class="shift">शाम 🌇</div>
        <div class="name" id="name2"></div>
        <div class="info" id="info2"></div>
      </div>
    </div>
    <div class="box-group">
      <div class="box-heading">Night</div>
      <div class="box box3">
        <div class="shift">रात 🌙</div>
        <div class="name" id="name3"></div>
        <div class="info" id="info3"></div>
      </div>
    </div>
    <div class="box-group">
      <div class="box-heading">(JSY) On Duty Staff</div>
      <div class="box box4">
        <div class="shift" id="shift4">शिफ्ट 🔄</div>
        <div class="name" id="name4"></div>
        <div class="info" id="info4"></div>
      </div>
    </div>
  </div>

  <h2>S.N.C.U.- O.T. Staff Auto-update Duty Chart</h2>
  <div class="boxes-row">
    <div class="box-group">
      <div class="box-heading">Morning</div>
      <div class="box box1">
        <div class="shift">सुबह ☀️</div>
        <div class="name" id="name5"></div>
        <div class="info" id="info5"></div>
      </div>
    </div>
    <div class="box-group">
      <div class="box-heading">Evening</div>
      <div class="box box2">
        <div class="shift">शाम 🌇</div>
        <div class="name" id="name6"></div>
        <div class="info" id="info6"></div>
      </div>
    </div>
    <div class="box-group">
      <div class="box-heading">Night</div>
      <div class="box box3">
        <div class="shift">रात 🌙</div>
        <div class="name" id="name7"></div>
        <div class="info" id="info7"></div>
      </div>
    </div>
    <div class="box-group">
      <div class="box-heading">(S.N.C.U.- O.T.) On Duty Staff</div>
      <div class="box box4">
        <div class="shift" id="shift8">शिफ्ट 🔄</div>
        <div class="name" id="name8"></div>
        <div class="info" id="info8"></div>
      </div>
    </div>
  </div>

  <script>
    const firstMorning = [ "Neha Tripathi", "Kiran Singh", "Mehrun Nisha", "Malti Devi", "Shamima Khatoon"];
    const firstEvening = [ "Shamima Khatoon", "Neha Tripathi", "Kiran Singh", "Mehrun Nisha", "Malti Devi"];
    const firstNight = [ "Malti Devi", "Shamima Khatoon", "Neha Tripathi", "Kiran Singh", "Mehrun Nisha"];
    const secondMorning = ["Kiran Singh", "Mehrun Nisha", "Malti Devi", "Shamima Khatoon","Neha Tripathi"];
    const baseSecondEvening = [ "Mehrun Nisha", "Malti Devi", "Shamima Khatoon ", "Neha Tripathi","Kiran Singh"];
    const secondNight = ["Vibha", "Sheeba"];
    const weekdaysHindi = ["रविवार", "सोमवार", "मंगलवार", "बुधवार", "गुरुवार", "शुक्रवार", "शनिवार"];

    function getMonthWeekNumber(today) {
      const day = today.getDay();
      const daysSinceMonday = (day + 6) % 7;
      const mondayThisWeek = new Date(today);
      mondayThisWeek.setDate(today.getDate() - daysSinceMonday);
      const firstOfMonth = new Date(today.getFullYear(), today.getMonth(), 1);
      const diffDays = Math.floor((mondayThisWeek - firstOfMonth) / (1000 * 60 * 60 * 24));
      return Math.floor(diffDays / 7);
    }

    function updateBoxes() {
  const now = new Date();
  const weekNumRaw = getMonthWeekNumber(now);
  const dayOfWeek = now.getDay();
  const hour = now.getHours();

  // ✅ Monday 8AM Fix:
  let weekNum = weekNumRaw;
  if (dayOfWeek === 1 && hour < 8) {
    weekNum = weekNumRaw - 1;
  }

  // 👇 बाकी सब वही
  const index1 = weekNum % firstMorning.length;
  const index2 = weekNum % firstEvening.length;
  const index3 = weekNum % firstNight.length;
  const index5 = weekNum % secondMorning.length;
  const index7 = weekNum % secondNight.length;
  const index6 = weekNum % baseSecondEvening.length;

  const nightOnDuty = secondNight[index7];
  const nightOffDuty = secondNight.filter(name => name !== nightOnDuty)[0];
  const finalSecondEvening = [baseSecondEvening[index6], nightOffDuty];
  const todayName = weekdaysHindi[dayOfWeek];

  document.getElementById("name1").innerText = firstMorning[index1];
  document.getElementById("info1").innerText = `सप्ताह ${weekNum + 1} | ${todayName}`;
  document.getElementById("name2").innerText = firstEvening[index2];
  document.getElementById("info2").innerText = `सप्ताह ${weekNum + 1} | ${todayName}`;
  document.getElementById("name3").innerText = firstNight[index3];
  document.getElementById("info3").innerText = `सप्ताह ${weekNum + 1} | ${todayName}`;

  let current1, shift1;
  if (hour >= 8 && hour < 15) { current1 = firstMorning[index1]; shift1 = "सुबह ☀️"; }
  else if (hour >= 15 && hour < 22) { current1 = firstEvening[index2]; shift1 = "शाम 🌇"; }
  else { current1 = firstNight[index3]; shift1 = "रात 🌙"; }
  document.getElementById("name4").innerText = current1;
  document.getElementById("shift4").innerText = shift1;
  document.getElementById("info4").innerText = `समय ${hour} | ${todayName}`;

  document.getElementById("name5").innerText = secondMorning[index5];
  document.getElementById("info5").innerText = `सप्ताह ${weekNum + 1} | ${todayName}`;
  document.getElementById("name6").innerText = finalSecondEvening.join(", ");
  document.getElementById("info6").innerText = `सप्ताह ${weekNum + 1} | ${todayName}`;
  document.getElementById("name7").innerText = nightOnDuty;
  document.getElementById("info7").innerText = `सप्ताह ${weekNum + 1} | ${todayName}`;

  let current2, shift2;
  if (hour >= 8 && hour < 14) { current2 = secondMorning[index5]; shift2 = "सुबह ☀️"; }
  else if (hour >= 14 && hour < 20) { current2 = finalSecondEvening.join(", "); shift2 = "शाम 🌇"; }
  else { current2 = nightOnDuty; shift2 = "रात 🌙"; }
  document.getElementById("name8").innerText = current2;
  document.getElementById("shift8").innerText = shift2;
  document.getElementById("info8").innerText = `समय ${hour} | ${todayName}`;
}

    updateBoxes();
    setInterval(updateBoxes, 1000);
  </script>
</body>
</html>
