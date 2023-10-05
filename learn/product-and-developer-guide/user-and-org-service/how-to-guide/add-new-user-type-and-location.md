---
description: 'How to add user-type and location details for a state:'
---

# Add new user type & location

New user-type, sub-type and location is added into the system by using the form-api, the below link contains the present system user-types and sub-types details.\


{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1911291950/SB-21854+User+Type+and+Sub+Type+for+logged+in+users" %}
User-Type and Sub-Types breif info\
\

{% endembed %}

{% file src="../../../../.gitbook/assets/UserTypes-SB.pdf" %}
Configure user-type and location
{% endfile %}

\
Form read-api response:

```json
{
    "id": "api.form.read",
    "params": {
        "resmsgid": "22290189-5778-44f7-80c9-2d1cb10e2616",
        "msgid": "c304da4f-7e39-49a9-ae74-159f95356145",
        "status": "successful"
    },
    "responseCode": "OK",
    "result": {
        "form": {
            "type": "profileconfig_v2",
            "subtype": "28",
            "action": "get",
            "component": "*",
            "framework": "*",
            "data": {
                "templateName": "profileconfig_v2",
                "action": "get",
                "fields": [
                    {
                        "code": "name",
                        "type": "input",
                        "templateOptions": {
                            "labelHtml": {
                                "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                "values": {
                                    "$0": "Name"
                                }
                            },
                            "hidden": true,
                            "placeHolder": "Enter Name",
                            "multiple": false
                        },
                        "validations": [
                            {
                                "type": "required"
                            }
                        ]
                    },
                    {
                        "code": "persona",
                        "type": "nested_select",
                        "templateOptions": {
                            "hidden": true,
                            "labelHtml": {
                                "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                "values": {
                                    "$0": "Role"
                                }
                            },
                            "placeHolder": "Select Role",
                            "multiple": false,
                            "dataSrc": {
                                "marker": "SUPPORTED_PERSONA_LIST"
                            }
                        },
                        "validations": [
                            {
                                "type": "required"
                            }
                        ],
                        "children": {
                            "administrator": [
                                {
                                    "code": "state",
                                    "type": "select",
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "State"
                                            }
                                        },
                                        "placeHolder": "Select State",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "STATE_LOCATION_LIST",
                                            "params": {
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "subPersona",
                                    "type": "select",
                                    "default": null,
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "Subrole"
                                            }
                                        },
                                        "placeHolder": "Select Subrole",
                                        "multiple": true,
                                        "dataSrc": {
                                            "marker": "SUBPERSONA_LIST",
                                            "params": {
                                                "useCase": "SIGNEDIN"
                                            }
                                        },
                                        "options": [
                                            {
                                                "value": "hm",
                                                "label": "HM"
                                            },
                                            {
                                                "value": "crp",
                                                "label": "CRP"
                                            },
                                            {
                                                "value": "chm",
                                                "label": "Complex HM"
                                            },
                                            {
                                                "value": "meo",
                                                "label": "MEO"
                                            },
                                            {
                                                "value": "dyeo",
                                                "label": "DyEO"
                                            },
                                            {
                                                "value": "atwo",
                                                "label": "ATWO"
                                            },
                                            {
                                                "value": "dtwo",
                                                "label": "DTWO"
                                            },
                                            {
                                                "value": "gcdo_pmrc",
                                                "label": "GCDO PMRC"
                                            },
                                            {
                                                "value": "cmo_pmrc",
                                                "label": "CMO PMRC"
                                            },
                                            {
                                                "value": "amo_pmrc",
                                                "label": "AMO PMRC"
                                            },
                                            {
                                                "value": "ddtw",
                                                "label": "DDTW"
                                            },
                                            {
                                                "value": "aso_dpo",
                                                "label": "ASO DPO"
                                            },
                                            {
                                                "value": "asst_als_coordinator",
                                                "label": "Asst ALS Coordinator"
                                            },
                                            {
                                                "value": "asst_ie_coordinator",
                                                "label": "Asst IE Coordinator"
                                            },
                                            {
                                                "value": "als_coordinator",
                                                "label": "ALS Coordinator"
                                            },
                                            {
                                                "value": "ie_coordinator",
                                                "label": "IE Coordinator"
                                            },
                                            {
                                                "value": "cmo",
                                                "label": "CMO"
                                            },
                                            {
                                                "value": "aamo",
                                                "label": "AAMO"
                                            },
                                            {
                                                "value": "amo",
                                                "label": "AMO"
                                            },
                                            {
                                                "value": "apc",
                                                "label": "APC"
                                            },
                                            {
                                                "value": "diet_lecturer",
                                                "label": "DIET Lecturer"
                                            },
                                            {
                                                "value": "diet_pricipal",
                                                "label": "DIET Principal"
                                            },
                                            {
                                                "value": "deo",
                                                "label": "DEO"
                                            },
                                            {
                                                "value": "rjd",
                                                "label": "RJD"
                                            },
                                            {
                                                "value": "slcc",
                                                "label": "SLCC"
                                            },
                                            {
                                                "value": "slmo",
                                                "label": "SLMO"
                                            },
                                            {
                                                "value": "spd",
                                                "label": "SPD"
                                            },
                                            {
                                                "value": "dir_ad_ed",
                                                "label": "Director Adult Education"
                                            },
                                            {
                                                "value": "dir_pub_lib",
                                                "label": "Director Public Libraries"
                                            },
                                            {
                                                "value": "dir_scert",
                                                "label": "Director SCERT"
                                            },
                                            {
                                                "value": "sec_kgbv",
                                                "label": "Secretary KGBV"
                                            },
                                            {
                                                "value": "sec_pub_lib",
                                                "label": "Secretary Public Libraries"
                                            },
                                            {
                                                "value": "dep_dir_ad_ed",
                                                "label": "Deputy director Adult Education"
                                            },
                                            {
                                                "value": "lib_pub_lib",
                                                "label": "Librarian Public Libraries"
                                            },
                                            {
                                                "value": "sup_ad_ed",
                                                "label": "Supervisor Adult Education"
                                            },
                                            {
                                                "value": "lib_bdc",
                                                "label": "Librarian Public Libraries/ Book deposit center"
                                            },
                                            {
                                                "value": "ins_ad_ed",
                                                "label": "Instructor/ Volunteer Adult Education"
                                            },
                                            {
                                                "value": "bdc_inch",
                                                "label": "BDC Incharge"
                                            }
                                        ]
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "district",
                                    "type": "select",
                                    "context": "state",
                                    "default": null,
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "District"
                                            }
                                        },
                                        "placeHolder": "Select District",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "district",
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "block",
                                    "type": "select",
                                    "context": "district",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "Block",
                                        "placeHolder": "Select Block",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "block",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    },
                                    "validations": []
                                },
                                {
                                    "code": "school",
                                    "type": "select",
                                    "context": "block",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "School",
                                        "placeHolder": "Select School",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "school",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    }
                                }
                            ],
                            "teacher": [
                                {
                                    "code": "state",
                                    "type": "select",
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "State"
                                            }
                                        },
                                        "placeHolder": "Select State",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "STATE_LOCATION_LIST",
                                            "params": {
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "district",
                                    "type": "select",
                                    "context": "state",
                                    "default": null,
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "District"
                                            }
                                        },
                                        "placeHolder": "Select District",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "district",
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "block",
                                    "type": "select",
                                    "context": "district",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "Block",
                                        "placeHolder": "Select Block",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "block",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    },
                                    "validations": []
                                },
                                {
                                    "code": "school",
                                    "type": "select",
                                    "context": "block",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "School",
                                        "placeHolder": "Select School",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "school",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    }
                                }
                            ],
                            "student": [
                                {
                                    "code": "state",
                                    "type": "select",
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "State"
                                            }
                                        },
                                        "placeHolder": "Select State",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "STATE_LOCATION_LIST",
                                            "params": {
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "district",
                                    "type": "select",
                                    "context": "state",
                                    "default": null,
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "District"
                                            }
                                        },
                                        "placeHolder": "Select District",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "district",
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "block",
                                    "type": "select",
                                    "context": "district",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "Block",
                                        "placeHolder": "Select Block",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "block",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    },
                                    "validations": []
                                },
                                {
                                    "code": "cluster",
                                    "type": "select",
                                    "context": "block",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "Cluster",
                                        "placeHolder": "Select Cluster",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "cluster",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    }
                                },
                                {
                                    "code": "school",
                                    "type": "select",
                                    "context": "cluster",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "School",
                                        "placeHolder": "Select School",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "school",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    }
                                }
                            ],
                            "other": [
                                {
                                    "code": "state",
                                    "type": "select",
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "State"
                                            }
                                        },
                                        "placeHolder": "Select State",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "STATE_LOCATION_LIST",
                                            "params": {
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "district",
                                    "type": "select",
                                    "context": "state",
                                    "default": null,
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "District"
                                            }
                                        },
                                        "placeHolder": "Select District",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "district",
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "block",
                                    "type": "select",
                                    "context": "district",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "Block",
                                        "placeHolder": "Select Block",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "block",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    },
                                    "validations": []
                                },
                                {
                                    "code": "cluster",
                                    "type": "select",
                                    "context": "block",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "Cluster",
                                        "placeHolder": "Select Cluster",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "cluster",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    }
                                },
                                {
                                    "code": "school",
                                    "type": "select",
                                    "context": "cluster",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "School",
                                        "placeHolder": "Select School",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "school",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    }
                                }
                            ],
                            "parent": [
                                {
                                    "code": "state",
                                    "type": "select",
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "State"
                                            }
                                        },
                                        "placeHolder": "Select State",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "STATE_LOCATION_LIST",
                                            "params": {
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "district",
                                    "type": "select",
                                    "context": "state",
                                    "default": null,
                                    "templateOptions": {
                                        "labelHtml": {
                                            "contents": "<span>$0&nbsp;<span class=\"required-asterisk\">*</span></span>",
                                            "values": {
                                                "$0": "District"
                                            }
                                        },
                                        "placeHolder": "Select District",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "district",
                                                "useCase": "SIGNEDIN_GUEST"
                                            }
                                        }
                                    },
                                    "validations": [
                                        {
                                            "type": "required"
                                        }
                                    ]
                                },
                                {
                                    "code": "block",
                                    "type": "select",
                                    "context": "district",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "Block",
                                        "placeHolder": "Select Block",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "block",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    },
                                    "validations": []
                                },
                                {
                                    "code": "cluster",
                                    "type": "select",
                                    "context": "block",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "Cluster",
                                        "placeHolder": "Select Cluster",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "cluster",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    }
                                },
                                {
                                    "code": "school",
                                    "type": "select",
                                    "context": "cluster",
                                    "default": null,
                                    "templateOptions": {
                                        "label": "School",
                                        "placeHolder": "Select School",
                                        "multiple": false,
                                        "dataSrc": {
                                            "marker": "LOCATION_LIST",
                                            "params": {
                                                "id": "school",
                                                "useCase": "SIGNEDIN"
                                            }
                                        }
                                    }
                                }
                            ]
                        }
                    }
                ]
            },
            "created_on": "2021-11-23T04:50:35.931Z",
            "last_modified_on": null,
            "rootOrgId": "*"
        }
    },
    "ts": "2023-07-04T13:06:52.153Z",
    "ver": "1.0"
}
```
