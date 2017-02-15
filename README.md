# Hello
ทดลองใช้ Git command จาก https://gist.github.com/norsez/3016877

Git

Git เป็น revision control แบบ distributed และ แบบ non-linear history 

clone

repository ใน GitHub https://github.com/norsez/projectA   clone

clone Vs. checkout

Git เป็นการ clone ทั้งตัว repository และ working directory  โดย origin repository (หรือ remote repository)  ที่ถูก clone มาเรียกว่า local repository
การทำ Git checkout จาก local repository คือทำที่  working directory เท่านั้น ไม่สามารถทำได้จาก origin repository

add, commit

หากเปลี่ยนแปลงไฟล์ใน local repository ที่ clone มา จะมีแต่ไฟล์ที่ใน Index เท่านั้นที่สามารถบันทีกลง history โดยใช้คำสั่ง add เพิ่มไฟล์ลงไปใน Index ของ Git

จากนั้นใช้คำสั่ง commit เพื่อให้ไฟล์ใน Index บันทีกการเปลี่ยนแปลง ส่วน  commit จะทำงานไปยัง local repository ที่ clone มาเท่านั้น ไม่มีผลไปถีง origin repository

push

หลังจากเราทำงานไปได้พักนีง เราควรจะส่ง history ใหม่ๆจาก local repository กลับไปยัง origin repository ที่ GitHub สามารถใช้ push

เพื่อ copy history กลับไปยัง origin repository

fetch, pull, merge

ในกรณีการทำงานเป็นทีม origin repository มีการเปลียนแปลงระหว่างที่ยังไม่ได้ push ควร fetch ก่อน  และ working directory จะไม่เปลี่ยนแปลงตาม Fetch  
หรือสามารถใช้ pull ดึงสิ่งใหม่ๆจาก origin repository มา merge ทั้งบน local repository และ working directory โดยทันที หากเกิด conflict จากการ merge ใน working directory จะต้อง resolve conflict ก่อน commit ต่อไป

สรุป pull คือ fetch และ merge 

reset

คือเอา working directory ก่อน commit มาใช้ ทำให้ history ของ local repository ใช้ ด้วยการ reset แต่ละ commit ใน Git จะมีเลข id ของ hash เช่น

29a4c0d0549897bf2dabc90a4f7664de31d4df43 
แต่สามารถใช้เลขเจ็ดตัวแรก

29a4c0d
เวลา reset ไปยัง commit id ใด สามารถกำหนดได้ว่า จะมี path หรือ file ไหนถูก reset บ้าง 

branch

ใน Git ใช้คำสั่ง branch เพื่อแตก branch ใหม่ออกมา

branch ใหม่ที่แยกออกมาก็จะมี history เป็นของมันเอง เราสามารถ checkout และ commit สิ่งใหม่ๆใน branch ได้ นั่นคือ ก็เหมือนใน local repository หนี่งๆ สามารถมี sub repository ย่อยๆ เรียก sub repository พวกนี้ว่า branch

เมื่อการแก้ master branch เสร็จแล้ว สามารถใช้คำสั่ง merge รวม master กับ new features branch เข้าด้วยกัน ซึ่งไม่ต่างจากการ merge remote และ local repository 

stash

เวลา pull หรือ fetch ต้อง merge เพราะมีการเปลี่ยนแปลงใน working directory บางครั้งไม่อยาก merge ณ ขณะนั้น เพราะจริงๆเรารู้ว่าเรา commit หลังจากสิ่งที่ pull หรือ fetch ก็ได้

ใน Git สามารถทำการ merge ได้ด้วยการ stash สิ่งที่จะ commit เพื่อซ่อนไม่ให้ pull หรือ fetch เห็นและจะบังคับเรา merge พอเรา pull หรือ fetch เสร็จแล้ว เราสามารถดีงสิ่งที่ซ่อนไว้ใน stash กลับมา เพื่อการ commit อย่างราบรื่นต่อไป

Fork 

fork คือการเอางาน open source มา โดยที่ปรับปรุงให้ต่างจาก open source เดิม ใน GitHub ใช้คำสั่ง fork  โดยกดปุ่มบน GitHub และสามารถจัดการโปรเจคที่ fork มาได้ด้วย เช่น push สิ่งที่ทำกลับไปที่โปรเจค GitHub นั้นสามารถทำได้ง่าย

Git SVN Bridge คืออะไร

Origin repository ของ cloned repository ไม่จำเป็นต้องเป็น Git repository origin อาจจะเป็น SVN repository ซึ่งมี Git SVN Bridge เพื่อใช้ความสามารถของ Git ในการทำงานกับ repoหระนพั ที่เป็น SVN ได้
