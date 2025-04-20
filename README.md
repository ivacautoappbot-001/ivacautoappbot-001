- 👋 Hi, I’m @ivacautoappbot-001
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
ivacautoappbot-001/ivacautoappbot-001 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->// ==UserScript==
// @name        AutoLoadFile
// @namespace   TKP
// @match       *://payment.ivacbd.com/*
// @grant       none
// @version     1.0
// @author      -T
// @description 1/3/2025, 2:36:57 AM
// ==/UserScript==

(function () {

    const mobileNumber = ''
    const password = ''
    const webFile1 = ''
    const fullName1 = ''
    const emailAddress = ''
    const webFile2 = ''
    const fullName2 = ''
    const visitPurpose = '.'
    const family_count = '';
    const visa_type = '';




    function hiComEqValue(file) {
        let webFile = file
        let fileChar = webFile.substring(0, 4);
        let eqValue;

        switch (fileChar) {
            case 'BGDK':
                eqValue = 'Khulna';
                break;
            case 'BGDD':
                eqValue = 'Dhaka';
                break;
            case 'BGDR':
                eqValue = 'Rajshahi';
                break;
            case 'BGDS':
                eqValue = 'Sylhet';
                break;
            case 'BGDC':
                eqValue = 'Chittagong';
                break;
            default:
                eqValue = 'Dhaka';
        }
        return eqValue;
    }

    function ivac_id_Value(file) {
        let webFile = file
        let fileChar = webFile.substring(0, 4);
        let eqValue;
        switch (fileChar) {
            case 'BGDK':
                eqValue = 'IVAC, KHULNA';
                break;
            case 'BGDD':
                eqValue = 'IVAC, Dhaka (JFP)';
                break;
            case 'BGDR':
                eqValue = 'IVAC , RAJSHAHI';
                break;
            default:
                eqValue = 'IVAC, Dhaka (JFP)';
        }
        return eqValue;
    }

    function setInputValue(selector, value) {
        let inputField = document.querySelector(selector);
        if (inputField) {
            inputField.value = value;
            console.log(`Value set for ${selector}:`, value);
            return true;
        } else {
            console.error(`Element not found for selector: ${selector}`);
            return false;
        }
    }

    function processButtonClick(selector) {
        let processButtonIdValue = document.getElementById(selector);
        if (processButtonIdValue) {

            processButtonIdValue.click();


        }
    }

    let applicationForm = document.getElementById("applicationForm");
    let formActionValue;
    if (applicationForm) {
        formActionValue = applicationForm.action
    }
    let baseUrl = 'https://payment.ivacbd.com/'
    let mobileVeryFy = baseUrl + 'mobile-verify'
    let mobileRegistration = baseUrl + 'registration-submit'
    let passwordSubmit = baseUrl + 'login-auth-submit'
    let otpSubmit = baseUrl + 'login-otp-submit'
    let applicationInfoSubmit = baseUrl + 'application-info-submit'
    let paynowSubmit = baseUrl + 'paynow'


    function autoselecFieldAuto(selector, selecttext) {
        let highcomInterval = setInterval(function () {
            let selectBox = document.querySelector(selector);
            let = optionsLenth = selectBox.options.length
            if (optionsLenth > 1) {

                for (let option of selectBox.options) {
                    if (option.text === selecttext) {
                        option.selected = true;
                        let event = new Event("change", { bubbles: true });
                        selectBox.dispatchEvent(event);
                        break;
                    }
                }

                clearInterval(highcomInterval);
            }
        }, 500);
    }



    if (formActionValue == applicationInfoSubmit) {


        autoselecFieldAuto('select[name="highcom"]', hiComEqValue(webFile1));
        autoselecFieldAuto('select[name="ivac_id"]', ivac_id_Value(webFile1));
        autoselecFieldAuto('select[name="visa_type"]', visa_type);
        autoselecFieldAuto('select[name="family_count"]', family_count);


        setTimeout(function () {
            setInputValue('input[name="webfile_id"]', webFile1);
            setInputValue('input[name="webfile_id_repeat"]', webFile1);
            setInputValue('textarea[name="visit_purpose"]', visitPurpose);
            let buttonClickCheck = document.querySelector('textarea[name="visit_purpose"]')
            if (buttonClickCheck != '') {
                let processButton = document.getElementById('submitButton')
                processButton.removeAttribute('disabled')
                processButtonClick('submitButton')
            }
        }, 1001);


    }


    if (formActionValue == mobileVeryFy) {

        let mobileInput = setInputValue("input[name='mobile_no']", mobileNumber);
        if (mobileInput) {
            processButtonClick('submitButton')
        }

    }

    if (formActionValue == mobileRegistration) {
        setInputValue("input[name='full_name']", fullName1);
        setInputValue("input[name='email']", emailAddress);
        setInputValue("input[name='password']", webFile1);
        setInputValue("input[name='password_confirmation']", webFile1);

    }


    if (formActionValue == passwordSubmit) {
        setInputValue("input[name='password']", password);
        processButtonClick('submitButton')
    }
    if (formActionValue == otpSubmit) {

        let loginOtpVerify = setInterval(() => {

            let otpCheck = document.querySelector("input[name='otp']");

            if (otpCheck.value.length == 6) {
                processButtonClick('submitButton')
                console.log("OTP Sublit...")
            } else {
                console.log("OTP Type Please")
            }

        }, 1001);

    }




    setTimeout(function () {
        let personalInfoAction = document.querySelector('form[name="PersonalForm"]')

        if (personalInfoAction) {
            if (personalInfoAction.action == baseUrl + 'personal-info-submit') {
                if (family_count > 0) {
                    let fullName = setInputValue("input[name='family[1][name]']", fullName2);
                    setInputValue("input[name='family[1][webfile_no]']", webFile2);
                    setInputValue("input[name='family[1][again_webfile_no]']", webFile2)
                }


                if ( family_count == 0 || fullName) {
                    let saveContinue = document.querySelector('button')

                    if (saveContinue.textContent == 'Save and show overview') {
                        saveContinue.click();
                    }
                }
            }
        }


    }, 1201);

    setTimeout(function () {
        let overviewFormAction = document.querySelector('form[name="overviewForm"]')
        if (overviewFormAction) {
            if (overviewFormAction.action == baseUrl + 'overview-submit') {
                let tos_agree = document.getElementById('tos_agree');
                if (tos_agree) {
                    tos_agree.checked = true;
                    let saveContinue = document.querySelector('button')
                    saveContinue.removeAttribute('disabled')
                    if (saveContinue) {
                        saveContinue.click();
                    }
                }

            }
        }


    }, 1201);




    function dateTimeSelect(selector, clearIntValue) {
        let selectBox = document.querySelector(selector);
        if (selectBox) {
            var options = Array.from(selectBox.options)
            if (options.length > 1 ) {
                options[1].selected = true;
                selectBox.dispatchEvent(new Event("change"));
            }
          if(options[1].selected){
            clearInterval(clearIntValue)
          }
        }
    }

    let paymentFormAction = document.querySelector('form[name="payment"]')
    let paymentFormActionValue;
    if (paymentFormAction) {
        paymentFormActionValue = paymentFormAction.action
    }



    if (paymentFormActionValue == paynowSubmit) {


        let paymentSelect = document.querySelectorAll('.payment_list .payment-option')
        if (paymentSelect) {
            paymentSelect[1].click()
        }

        let sendOtpButtonInterval = setInterval(function () {

            let sendOtpButton = document.getElementById('send-otp-btn')
            if (sendOtpButton) {
                let paymentOption = document.querySelectorAll('.payment-option')
                paymentOption[1].click()
                sendOtpButton.click()
                clearInterval(sendOtpButtonInterval)
            }

        }, 1201);




        let sendOtpVerify = setInterval(() => {

            let sendOtpInput = document.getElementById('otp-input')
            let verifyOtpBtn = document.getElementById('verify-otp-btn')

            if (sendOtpInput.value.length == 6) {
                if (verifyOtpBtn) {
                    verifyOtpBtn.click()
                    clearInterval(sendOtpVerify)
                }
            } else {

            }


        }, 1201);

        let appointmentDateInterval = setInterval(function () {
        dateTimeSelect('select[name="appointment_date"]', appointmentDateInterval)


        }, 1001);
        let appointmentTimeInterval = setInterval(function () {
        dateTimeSelect('select[name="appointment_time"]', appointmentTimeInterval)


        }, 1001);

    }

    let gettimeOutHeaddingInterval = setInterval(function () {
        let gettimeOutHeadding = document.querySelector('h1')
        let error500 = document.querySelector('.code')
        if (gettimeOutHeadding ){
          let gettimeOut = gettimeOutHeadding.innerText

          if (gettimeOut != 'Application fee change notice') {
              location.reload()
              clearInterval(gettimeOutHeaddingInterval)
          }

          if( error500){
            let error500Text = error500.innerText
            if(error500Text == '500'){
              location.reload()
              clearInterval(gettimeOutHeaddingInterval)
            }
          }

        }



    }, 1001);







})();



