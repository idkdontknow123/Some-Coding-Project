
const output = document.getElementById("terminalOutput");

input.addEventListener("keypress", function(e) {
    if (e.key === "Enter") {
        const command = input.value.trim();
        output.innerHTML += `<div>> ${command}</div>`; // Echo the command

        let simulatedOutput = "";

        switch (command.toLowerCase()) {
            case "dir":
                simulatedOutput = "<div>Volume in drive C has no label.</div><div>Directory of C:\\</div><br><div>05/10/2025  05:00 PM    <DIR>          Documents</div><div>05/10/2025  05:05 PM    <DIR>          Projects</div><div>05/10/2025  05:10 PM             1,234  report.txt</div>";
                break;
            case "help":
                simulatedOutput = "<div>Available commands: dir, help, echo [text]</div>";
                break;
            case command.startsWith("echo ") ? command.split(" ")[0] : "":
                simulatedOutput = `<div>${command.substring(5)}</div>`;
                break;
            default:
                simulatedOutput = `<div>'${command}' is not recognized as an internal or external command, operable program or batch file.</div>`;
        }

        output.innerHTML += simulatedOutput;
        input.value = ""; // Clear the input field
        output.scrollTop = output.scrollHeight; // Scroll to the bottom
    }
});
