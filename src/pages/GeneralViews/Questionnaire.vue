<template>
  <div class="col-sm-6 offset-sm-3 pt-lg-5">
    <survey :survey="survey"/>
  </div>
</template>
<script>
    import * as Survey from "survey-vue";
    import "survey-vue/survey.css";

    Survey.StylesManager.applyTheme("darkblue");

    export default {
        name: "surveyjs-component",
        data() {
            const json = {
                title: "SYMPTOMS ANALYSIS",
                showProgressBar: "bottom",
                showTimerPanel: false,
                firstPageIsStarted: true,
                startSurveyText: "Start Diagnosis",
                pages: [
                    {
                        questions: [
                            {
                                type: "html",
                                html: "You are about to start your Medical diagnosis to detect Coronavirus symptoms.<br/><br/>Information is still evolving.** Allergies, colds and flus can all trigger asthama, which can lead to shortening of breathe<br/>COVID-19 is the only one associated with shortness of breath on its own. Sources: Asthama and allergy foundation of America, World Health Organisation, Centres of disease control and Prevention<br/><br/>Please click on <b>'Start'</b> button when you are ready."
                            }
                        ]
                    }, {
                        questions: [
                            {
                                type: "radiogroup",
                                name: "cold",
                                title: "Are you experiencing cough?",
                                choices: [
                                    "Yes, Dry", "Yes, but Mild", "Yes, Wet", "No"
                                ],
                                correctAnswer: "",
                                covid: "Yes, Dry",
                                cold: "Yes, but Mild",
                                flu: "Yes, Dry",
                                allergy: "Yes, Dry"
                            }
                        ]
                    }, {
                        questions: [
                            {
                                type: "radiogroup",
                                name: "shortnessofbreath",
                                title: "Do you have shortness of breath",
                                choicesOrder: "random",
                                choices: [
                                    "Yes", "No", "Sometimes"
                                ],
                                correctAnswer: "",
                                covid: "Sometimes",
                                cold: "No",
                                flu: "No",
                                allergy: "No"

                            }
                        ]
                    }, {
                        questions: [
                            {
                                type: "radiogroup",
                                name: "sneeze",
                                title: "Do you often sneeze?",
                                choicesOrder: "random",
                                choices: [
                                    "Yes", "No"
                                ],
                                correctAnswer: "",
                                covid: "No",
                                cold: "Yes",
                                flu: "No",
                                allergy: "Yes"
                            }
                        ]
                    },
                    {
                        questions: [
                            {
                                type: "radiogroup",
                                name: "runningnose",
                                title: "Do you have runny or stuffy nose?",
                                choicesOrder: "random",
                                choices: [
                                    "Rarely", "Yes", "Sometimes", "No"
                                ],
                                correctAnswer: "",
                                covid: "Rarely",
                                cold: "Yes",
                                flu: "Sometimes",
                                allergy: "Yes"
                            }
                        ]
                    },
                ],
                
                completedHtml: "<h4 style=\"color:black;\">Your symptoms indicate you have <b>{correctedAnswers}</b> percent chances of COVID19 symptoms</b>.</h4>"
            };

            const survey = new Survey.Model(json);
            return {
                survey: survey
            };
        }
    };
</script>

<style>
h3, h5 {
  color: #32325d !important;
}
</style>
