alright so if i try to "add" with this command => 'node app.js add --title="Some title" --body="Some body"
it will create this => [{"title":"Some title","body":"Some body"}] in the notes-data.json file!
BUT!!
if i tried it one more time (!with different feed!) it basically crashed and i got this error => 'Cannot read property 'filter' of undefined'

Then i tried this in the notes.js file:
(orginal code)!!
et fetchNotes = () => {
    try{
        let notesString = fs.readFileSync('notes-data.json')
        notes = JSON.parse(notesString); 
    }catch(err){
        return []
    }
}

(edited code)!!
et fetchNotes = () => {
    try{
        let notesString = fs.readFileSync('notes-data.json') 
        notes = JSON.parse(notesString);
    }catch(err){
    
    }
    return []
}

so i basically moved the "return []" down..
than i ran the command => 'node app.js add --title="Some title" --body="Some body" > and it worked for the "first time" and when i tried it "the secound time" it worked too !BUT! i didn't "added" a new string i replaced the old one..


examples..
----------------------
(not moved the return)
[{"title":"Some title","body":"Some body"}] => 'Cannot read property 'filter' of undefined'
----------------------
(moved the return down)
 ran the command => [{"title":"Some title","body":"Some body"}] => everythink is okay
 2nd time i ran the command => [{"title":"Some title","body2":"Some body2"}] => i got it replaced by the old one

 what i wanted to get..
 [{"title":"Some title","body":"Some body"}], [{"title":"Some title","body2":"Some body2"}] =>
 i just go the [{"title":"Some title","body":"Some body"}] replaced by [{"title":"Some title","body2":"Some body2"}]
----------------------
 
