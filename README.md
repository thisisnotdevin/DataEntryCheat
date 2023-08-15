# DataEntryCheat



// This code is designed to check off specific checkboxes related to Timesheets required, Timesheets Approved,
// and POC duties with IDs 101, 106, 108, 111, 201, and 511.
// Creator: Devin Lin

var validatePaperDutyCheckbox = document.getElementById("uxUcDutySheet_uxchkValidatePaperDuty");
var timesheetReceivedCheckbox = document.getElementById("uxUcDutySheet_uxchkTimesheetReceived");

if (!validatePaperDutyCheckbox.checked) {
    validatePaperDutyCheckbox.click();
}

if (!timesheetReceivedCheckbox.checked) {
    timesheetReceivedCheckbox.click();
}
var checkboxes = [
    "chkOtherDuty3818",
    "chkOtherDuty3823",
    "chkOtherDuty3825",
    "chkOtherDuty3828",
    "chkOtherDuty3836",
    "chkOtherDuty3877"
];

for (var i = 0; i < checkboxes.length; i++) {
    var checkbox = document.getElementById(checkboxes[i]);
    
    if (!checkbox.checked) {
        checkbox.click();
    }
}

var scrollOffset = 300; // Adjust this value as needed
window.scrollTo(0, scrollOffset);

const setDropdownValue = (dropdownId, targetValues, delay) => {
    setTimeout(() => {
        const dropdown = document.getElementById(dropdownId);
        let selectedValue = null;

        for (const value of targetValues) {
            if (dropdown.querySelector(`option[value="${value}"]`)) {
                selectedValue = value;
                break;
            }
        }

        if (selectedValue !== null) {
            dropdown.value = selectedValue;
            dropdown.dispatchEvent(new Event("change", { bubbles: true }));
        }
    }, delay);
};

setDropdownValue("ddlReason", ["2242543", "926393"], 0); // Adjust delay if needed
setDropdownValue("ddlEditAction", ["1372593", "926395"], 400); // Adjust delay if needed


const submitIfConditionMet = () => {
    const condition = document.querySelector('#ddlEditAction').value === '1372593' || document.querySelector('#ddlEditAction').value === '926395';
    if (condition) {
        const inputSave = document.querySelector('input[type="submit"][value="Save"]');
        if (inputSave) {
            inputSave.click();
        }
    }
};

// Add an event listener to the ddlEditAction dropdown
const ddlEditActionDropdown = document.getElementById("ddlEditAction");
ddlEditActionDropdown.addEventListener("change", submitIfConditionMet);
