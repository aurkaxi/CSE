[[Journal/<%tp.date.now("YYYY-MM-DD",-1,tp.file.title,"YYYY-MM-DD")%>|Yesterday]] <-> [[Journal/<%tp.date.now("YYYY-MM-DD",1,tp.file.title,"YYYY-MM-DD")%>|Tomorrow]]

# Classes
<%*
  const dayOfWeek = Number(tp.date.now("d", 0, tp.file.title, "YYYY.MM.DD"));
  const dayOfMonth = Number(tp.date.now("D", 0, tp.file.title, "YYYY.MM.DD"));
  const month = Number(tp.date.now("M", 0, tp.file.title, "YYYY.MM.DD"));
  const year = Number(tp.date.now("YYYY", 0, tp.file.title, "YYYY.MM.DD"));
  const lastDayOfMonth = Number(month === 2 ? ((year % 4 === 0 && year % 100 !== 0) || year % 400 === 0 ? 29 : 28) : [4, 6, 9, 11].includes(month) ? 30 : 31);
  const doLastDOM = Boolean([1,2,3].includes(dayOfWeek) ? dayOfMonth === lastDayOfMonth : dayOfWeek == 4 ? dayOfMonth >= (lastDayOfMonth - 3) : false);
  
  if (dayOfWeek == 0) {
    // Sunday
-%>
### 0940 - 1030: Math-31**05**

### 1045 - 1135: CSE-31**04**

### 1225 - 0115: CSE-31**02**

### 0230 - 0500: CSE-31*11*

<%*
  }
  else if (dayOfWeek == 1) {
	// Monday
-%>
### 0940 - 1030: Math-31**05**

### 1045 - 1135: CSE-31**01**

### 1135 - 1225: CSE-31**03**

### 1225 - 0115: CSE-31**04**

### 0230 - 0500: CSE-31*13*
<%*
  }
  else if (dayOfWeek == 2) {
	// Tuesday
-%>
### 0940 - 1030: CSE-31**01**

### 1135 - 1225: CSE-31**02**

### 1225 - 0115: CSE-31**03**

<%*
  }
  else if (dayOfWeek == 3) {
	// Wednesday
-%>
### 0940 - 1030: Math-31**05**

### 1045 - 1135: CSE-31**01**

### 1225 - 0115: CSE-31**04**

### 0230 - 0500: CSE-31*16*

<%*
  }
  else if (dayOfWeek == 4) {
	// Thursday
-%>
### 1045 - 1135: CSE-31**03**

### 1225 - 0115: CSE-31**02**

<%*
  }
  else if (dayOfWeek == 5) {
	// Friday
-%>
### Friday Task
<%*
  }
  else if (dayOfWeek == 6) {
	// Saturday
-%>
### Saturday Task
<%*
  }
  
  // End of Month Tasks
  if (doLastDOM) {
-%>
### first End of Month task

<%*
  }
-%>
# Extra