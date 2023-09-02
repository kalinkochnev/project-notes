It is a command line tool that can parse json outputs.

# Examples
To extract the title and start date from a response like the following:
```json
{
  "status": "OK",
  "service": "AwardService",
  "response": {
    "body": [
      {
        "award": {
          "id": 10,
          "awardNumber": "1941529",
          "awardTitle": "NSF Engineering Research Center for the Internet of Things for Precision Agriculture (IoT4Ag)",
          "description": "Ensuring food, energy, and water security is a societal grand challenge. By 2050, the",
          "awardStartDate": "09/01/2020",
        }
	  }
	// ... more items in array
	],
  }
}
```

You would use the command
```bash
echo $json_output | jq '.response.body | [ .[] | {title: .award.awardTitle, start: .award.awardStartDate } ]
```
- Can extract keys with `.fieldname.subfield ` etc
- Pipes work as expected, output of a command gets passed to next
-  The `[ .[] | {title: .award.awardTitle, start: .award.awardStartDate } ]`  says to output a new array where for each object in the input, create a new `{}` where you get the `.award.awardTitle` and `.award.awardStartDate` from the input

**Example output**
```bash
[
  {
    "title": "IUCRC Phase I: South Dakota School of Mines and Technology: Center for Solid-State Electric Power Storage (CEPS)",
    "start": "07/01/2021"
  },
  {
    "title": "IRES Track 1: International Research Experiences for Students in AI-Enabled Decision Analytics for Advancing Air Taxi and Drone Operations",
    "start": "04/01/2023"
  },
  {
    "title": "IRES Track I: US-Finnish research on sustainable evolution and technical debt management in cloud-native systems",
    "start": "04/14/2023"
  },
  {
    "title": "REU Site: Summer Undergraduate Program in Engineering Research at Berkeley-Responsible Artificial Intelligence (SUPERB-RAI)",
    "start": "04/01/2020"
  },
  {
    "title": "NSF REU SITE: ASSET: Advanced Secured Sensor Enabling Technologies",
    "start": "03/01/2023"
  },
  {
    "title": "RII-BEC: Boosting Retention, Interest, and Diversity through Guided Experiences in STEM",
    "start": "09/01/2022"
  }
]
```