
<h1 style="font-family: 'Roboto', sans-serif; font-size: 18px; font-weight: 700; color: #34495E; text-align: center; text-transform: uppercase; letter-spacing: 2px; background: linear-gradient(45deg, #FF6F61, #FF3D00); -webkit-background-clip: text; color: transparent; padding: 20px 0; box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); border-radius: 10px; border: 2px solid #FF3D00;">
    Design One
</h1>

![[grid07.png]]


```tsx
.parent {
  height: 100vh;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: 90px 1fr 90px; 
}

.parent div:nth-child(1) {
  grid-column: 1 / -1; /* সব 12টি কলাম নিয়ে জায়গা দিচ্ছে */
}

.parent div:nth-child(2) {
  grid-column: 1 / 3; /* প্রথম দুটি কলাম নিয়ে জায়গা দিচ্ছে */
}

.parent div:nth-child(3) {
  grid-column: 3 / -1; /* তৃতীয় কলাম থেকে শুরু করে সব কলাম নিয়ে জায়গা দিচ্ছে */
}

.parent div:nth-child(4) {
  grid-column: 1 / -1; /* সব 12টি কলাম নিয়ে জায়গা দিচ্ছে */
}

```


<h1 style="font-family: 'Roboto', sans-serif; font-size: 18px; font-weight: 700; color: #34495E; text-align: center; text-transform: uppercase; letter-spacing: 2px; background: linear-gradient(45deg, #FF6F61, #FF3D00); -webkit-background-clip: text; color: transparent; padding: 20px 0; box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); border-radius: 10px; border: 2px solid #FF3D00;">
    Design Two
</h1>

![[grid08.png]]

```tsx
<div class="parent">
     <div>1</div>
     <div>2</div>
     <div>3</div>
     <div>4</div>
</div>


.parent{
  height:100vh;
  display:grid;

  grid-templete-colums:repeat(12,1fr);
  grid-template-row:90 1fr 90px;
}


.parent div:nth-child(1) {
    grid-column: 3 / -1;
}

.parent div:nth-child(2) {
   grid-column: 1 / 3;
   grid-row:1 / 3
}

.parent div:nth-child(3) {
   grid-column: 3 / -1;
}

.parent div:nth-child(4) {
    grid-column: 1 / -1;
}

```




