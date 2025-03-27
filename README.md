Below is the updated `README.md` file that incorporates all the instructions, including replacing `null` values with meaningful data, calculating fields like `duration`, and ensuring fields like `mealPlan` and `transportation` are filled according to predefined options.

---

# Camp Data Extraction Project

This repository contains structured data extracted from PDF files related to camp providers, camps, sessions, programs, and locations. The data is organized into JSON files and follows a hierarchical folder structure.

## Table of Contents

1. [Folder Structure](#folder-structure)
2. [Data Extraction Steps](#data-extraction-steps)
3. [JSON File Descriptions](#json-file-descriptions)
   - [camp_provider.json](#camp_providerjson)
   - [camp.json](#campjson)
   - [session.json](#sessionjson)
   - [program.json](#programjson)
   - [location.json](#locationjson)
4. [Categories and Subcategories](#categories-and-subcategories)
5. [Contribution Guidelines](#contribution-guidelines)

---

## Folder Structure

The data is organized in the following folder structure:

```
aanand-pdfA-20/
└── fairfox/ (represents the site name)
    ├── camp_provider.json
    ├── camp.json
    ├── session.json
    ├── program.json
    └── location.json
```

- **aanand-pdfA-p1-p2-20**: Represents the overall dataset.
  - `aanand`: Name of the candidate.
   - `pdfA`: Name of the PDF file.
  - `20`: Number of camp providers.
- **fairfox**: Represents the site name (e.g., Fairfax County Park Authority).
  - Contains five main JSON files: `camp_provider.json`, `camp.json`, `session.json`, `program.json`, and `location.json`.

---

## Data Extraction Steps

Follow these steps to extract and organize the data:

### Step 1: Extract `camp_provider.json`
- **Objective**: Extract information about the camp provider.
- **Fields to Extract**:
  - Name, profile image, site link, logo link, phone numbers, emails, and social media profiles.
- **Validation**:
  - Ensure all URLs are valid and complete.
  - Format phone numbers consistently (e.g., `+17032224664`).

### Step 2: Extract `camp.json`
- **Objective**: Extract information about individual camps offered by the camp provider.
- **Key Points**:
  - Use the `campProvider` name extracted in Step 1.
  - Ensure each camp has a unique name and description.
  - Map categories and subcategories accurately using the provided list.
- **Validation**:
  - Verify that `campProvider` matches the name in `camp_provider.json`.
  - Validate location details (address, zipcode, latitude, longitude).

### Step 3: Extract `session.json`
- **Objective**: Extract information about individual sessions within a camp.
- **Key Points**:
  - Use the `camp` name extracted in Step 2.
  - Ensure the session name exists within the corresponding camp.
  - Map categories and subcategories based on tags.
- **Validation**:
  - Verify that the `camp` name matches an existing entry in `camp.json`.
  - Ensure dates, duration, and eligibility criteria are consistent.

### Step 4: Extract `program.json`
- **Objective**: Extract information about individual programs within a session.
- **Key Points**:
  - Use the `camp` and `session` names extracted in Steps 2 and 3.
  - Ensure the program name exists within the corresponding session.
  - Map subcategories accurately.
- **Validation**:
  - Verify that the `camp` and `session` names match existing entries in `camp.json` and `session.json`.
  - Validate program-specific details like cost, duration, and eligibility.

### Step 5: Extract `location.json`
- **Objective**: Extract location details for camps, sessions, or programs.
- **Key Points**:
  - Ensure each location has a unique address.
  - Include latitude, longitude, zipcode, and city for accurate mapping.
- **Validation**:
  - Verify that all fields are complete and accurate.

---

## JSON File Descriptions

### camp_provider.json

This file contains information about the camp provider.

#### Example:
```json
{
  "name": "Fairfax County Park Authority",
  "profileImage": "https://www.fairfaxcountry.com/uploads/4/4/2/7/4427384/todd-sucherman-3_orig.png",
  "siteLink": "https://www.fairfaxcountry.com",
  "logoLink": "https://www.fairfaxcountry.com/uploads/4/4/2/7/4427384/editor/billboard-logo-1.png?1725651153",
  "phoneNumbers": [
      "2026437424"
  ],
  "emails": [
    "camps@fairfaxcounty.gov"
  ],
  "socials": [
    {
        "platform": "Instagram",
        "link": "https://www.instagram.com/openmic.ag"
    },
    {
        "platform": "Youtube",
        "link": "https://www.youtube.com/watch?feature=shared&v=GXd_oYi0hMc"
    },
    {
        "platform": "Instagram",
        "link": "http://www.instagram.com/7drumcity"
    },
    {
        "platform": "Instagram",
        "link": "http://www.instagram.com/thepocket_dc"
    },
    {
        "platform": "Instagram",
        "link": "http://www.instagram.com/flashband_dc"
    },
    {
        "platform": "Facebook",
        "link": "https://www.facebook.com/thepocketdc"
    },
    {
        "platform": "Instagram",
        "link": "https://www.instagram.com/thepocket_dc/"
    },
    {
        "platform": "Facebook",
        "link": "https://www.facebook.com/7drumcity"
    },
    {
        "platform": "Instagram",
        "link": "https://instagram.com/7drumcity"
    },
    {
        "platform": "Linkedin",
        "link": "https://linkedin.com/company/7drumcity"
    },
    {
        "platform": "Facebook",
        "link": "https://www.facebook.com/Flashband"
    },
    {
        "platform": "Instagram",
        "link": "https://www.instagram.com/flashband_dc/"
    }
]
}

```

#### Fields:
- **name**: Official name of the camp provider.
- **profileImage**: URL to the provider's profile image.
- **siteLink**: Provider's official website URL.
- **logoLink**: URL to the provider's logo.
- **phoneNumbers**: List of phone numbers in international format.
- **emails**: List of email addresses.
- **socials**: Social media profiles with platform names and links.

---

### camp.json

This file contains information about individual camps offered by the camp provider.

#### Example:
```json
{
  "campProvider": "Fairfax County Park Authority",
  "campType": "Spring Camp",
  "name": "Spring Camps Custom Worlds",
  "description": "Campers will explore game creation and bring their imagination to life...",
  "location": {
    "address": "12011 Government Center Pkwy, Fairfax, VA 22035, USA",
    "zipcode": "22035",
    "lat": 38.85525029999999,
    "long": -77.3625954
  },
  "categories": ["STEM"],
  "tags": ["game creation", "programming", "beginners"],
  "startDate": "2025-03-31",
  "endDate": "2025-04-01",
  "duration": 2,
  "eligibility": {
    "age": [8, 14],
    "grade": [3, 8],
    "gender": "co-ed"
  },
  "cost": 209,
  "deposit": 50,
  "other": {
    "mealPlan": "included",
    "transportation": "available"
  },
  "meetupType": "in-person",
  "startTime": 9,
  "endTime": 16
}
```

#### Fields:
- **campProvider**: Name of the organization running the camp.
- **campType**: Type of camp (e.g., Summer Camp, after school program).
- **name**: Official name of the camp.
- **description**: Detailed description of the camp.
- **location**: Address, zipcode, latitude, and longitude of the camp location.
- **categories**: Categories applicable to the camp (mapped from predefined categories).
- **tags**: Keywords or phrases relevant to the camp.
- **startDate**, **endDate**: Start and end dates of the camp.
- **duration**: Calculated as `(endDate - startDate) + 1` days.
- **eligibility**: Age, grade, and gender eligibility.
- **cost**: Total cost of attending the camp.
- **deposit**: Deposit amount required.
- **other**: Additional details like meal plans (`"included"`, `"not included"`) and transportation (`"available"`, `"not available"`).
- **meetupType**: Specifies if the camp is in-person or remote.
- **startTime**, **endTime**: Start and end times of the camp.

---

### session.json

This file contains information about individual sessions within a camp.

#### Example:
```json
{
  "camp": "Cake Wars 2.0",
  "name": "Cake Wars 2.0",
  "startDate": "2023-07-28",
  "endDate": "2023-08-01",
  "duration": 5,
  "categories": ["Culinary"],
  "tags": ["recipes", "breakfast foods", "drinks"],
  "cost": 445,
  "deposit": 100,
  "eligibility": {
    "age": [10, 14],
    "grade": null,
    "gender": "co-ed"
  },
  "description": "Cake Wars 2.0 is a culinary competition...",
  "location": {
    "address": "Woodburn ES",
    "zipcode": "22035",
    "lat": 38.85525029999999,
    "long": -77.3625954
  },
  "other": {
    "mealPlan": "not included",
    "transportation": "not available"
  },
  "meetupType": "in-person",
  "startTime": 9,
  "endTime": 16
}
```

#### Fields:
- **camp**: Name of the camp this session belongs to.
- **name**: Specific name of the session.
- **startDate**, **endDate**: Start and end dates of the session.
- **duration**: Calculated as `(endDate - startDate) + 1` days.
- **categories**: Categories applicable to the session.
- **tags**: Keywords or activities associated with the session.
- **cost**: Total cost of the session.
- **deposit**: Deposit amount required.
- **eligibility**: Age, grade, and gender eligibility.
- **description**: Detailed description of the session.
- **location**: Address, zipcode, latitude, and longitude of the session location.
- **other**: Additional details like meal plans and transportation.
- **meetupType**: Specifies if the session is in-person or remote.
- **startTime**, **endTime**: Start and end times of the session.

---

### program.json

This file contains information about individual programs within a session.

#### Example:
```json
{
  "camp": "Adventure Camp",
  "session": "Outdoor Adventure",
  "name": "Rock Climbing Workshop",
  "description": "Learn the basics of rock climbing...",
  "images": [
    "https://example.com/rock-climbing.jpg"
  ],
  "subCategories": ["Rock Climbing"],
  "tags": ["outdoor", "adventure", "kids"],
  "startDate": "2023-07-15",
  "endDate": "2023-07-20",
  "location": {
    "address": "Adventure Park, Fairfax, VA",
    "zipcode": "22035",
    "lat": 38.85525029999999,
    "long": -77.3625954
  },
  "duration": 6,
  "cost": 300,
  "deposit": 50,
  "eligibility": {
    "age": [8, 14],
    "grade": [3, 8],
    "gender": "co-ed"
  },
  "other": {
    "equipmentProvided": true,
    "insuranceRequired": false
  },
  "meetupType": "in-person",
  "startTime": 10,
  "endTime": 16
}
```

#### Fields:
- **camp**: Name of the camp offering the session.
- **session**: Name of the session this program belongs to.
- **name**: Official name of the program.
- **description**: Detailed description of the program.
- **images**: URLs linking to relevant images.
- **subCategories**: Subcategories associated with the program.
- **tags**: Keywords or phrases relevant to the program.
- **startDate**, **endDate**: Start and end dates of the program.
- **location**: Address, zipcode, latitude, and longitude of the program venue.
- **duration**: Calculated as `(endDate - startDate) + 1` days.
- **cost**: Total cost of attending the program.
- **deposit**: Deposit required to reserve a spot.
- **eligibility**: Age, grade, and gender eligibility.
- **other**: Additional details like equipment provided and insurance requirements.
- **meetupType**: Specifies if the program is in-person or remote.
- **startTime**, **endTime**: Start and end times of the program.

---

### location.json

This file contains detailed location information for camps, sessions, or programs.

#### Example:
```json
[
  {
    "address": "825 University Ave W, St Paul, MN 55104",
    "lat": 44.9560612,
    "long": -93.1351139,
    "zipcode": "55104",
    "city": "St Paul"
  }
]
```

#### Fields:
- **address**: Full address of the location.
- **lat**: Latitude coordinate of the location.
- **long**: Longitude coordinate of the location.
- **zipcode**: Postal code of the location.
- **city**: City where the location is situated.

---

## Categories and Subcategories

The following categories and subcategories are used to classify camps, sessions, and programs:

```json
categories_and_sub_categories =[
    {
        "Adventure": [
            "Hiking",
            "Rock Climbing",
            "Zip-lining",
            "Camping",
            "Canoeing",
            "Rappelling",
            "Survival Skills",
            "Nature Scavenger Hunt",
            "Stargazing"
        ]
    },
    {
        "Sports": [
            "Soccer",
            "Basketball",
            "Tennis",
            "Swimming",
            "Archery",
            "Martial Arts",
            "Badminton",
            "Water Polo",
            "Volleyball",
            "Ultimate Frisbee",
            "Bubble Soccer"
        ]
    },
    {
        "Arts": [
            "Painting",
            "Pottery",
            "Tie-Dye",
            "Jewelry Making",
            "Origami",
            "Woodworking",
            "Sand Art",
            "Graffiti Art",
            "Scrapbooking",
            "T-shirt Design"
        ]
    },
    {
        "STEM ": [
            "Robotics",
            "Coding",
            "3D Printing",
            "Drone Programming",
            "Science Experiments",
            "Astronomy",
            "Virtual Reality",
            "App Development",
            "DIY Electronics"
        ]
    },
    {
        "Music": [
            "Guitar",
            "Piano",
            "Drama Workshops",
            "Dance (Hip-hop, Ballet)",
            "Talent Shows",
            "Singing",
            "Musical Theater",
            "Stand-up Comedy",
            "Improv Games"
        ]
    },
    {
        "Nature": [
            "Bird Watching",
            "Wildlife Tracking",
            "Animal Care",
            "Beachcombing",
            "Insect Collection",
            "Marine Life Exploration",
            "Conservation Projects"
        ]
    },
    {
        "Academic": [
            "Math Puzzles",
            "Creative Writing",
            "Book Club",
            "Poetry Slam",
            "Public Speaking",
            "Debate Sessions",
            "Financial Literacy",
            "History Quizzes"
        ]
    },
    {
        "Culinary": [
            "Baking",
            "International Cooking",
            "Healthy Smoothie Making",
            "Food Science Experiments",
            "Recipe Creation",
            "Cupcake Decorating"
        ]
    },
    {
        "Linguistics": [
            "Language Games",
            "Cultural Dance",
            "Storytelling in a Foreign Language",
            "Language Exchange Sessions"
        ]
    },
    {
        "Leadership": [
            "Team-building Activities",
            "Leadership Challenges",
            "First Aid Training",
            "Confidence Building",
            "Public Speaking Workshops",
            "Debate Competitions"
        ]
    },
    {
        "Health": [
            "Yoga",
            "Meditation",
            "Mindfulness Exercises",
            "Sound Healing",
            "Nutrition Workshops",
            "Fitness Challenges",
            "DIY Spa Day"
        ]
    },
    {
        "Inclusion": [
            "Sensory Play",
            "Therapeutic Art",
            "Adaptive Sports",
            "Music Therapy",
            "Animal-assisted Therapy",
            "Inclusive Games"
        ]
    },
    {
        "Environmental": [
            "Recycling Projects",
            "Beach Clean-up",
            "Tree Planting",
            "Eco-friendly Crafts",
            "Composting",
            "Sustainable Gardening"
        ]
    },
    {
        "Travel": [
            "Map Reading",
            "Cultural Festivals",
            "Language Immersion",
            "City Tours",
            "Pen Pal Programs",
            "Global Music Exploration"
        ]
    },
    {
        "Equine": [
            "Horseback Riding",
            "Pet Training",
            "Horse Grooming",
            "Wildlife Observation",
            "Vet Workshops"
        ]
    },
    {
        "Cinematics": [
            "Digital Photography",
            "Video Editing",
            "Storyboarding",
            "Nature Photography",
            "Film-making",
            "Drone Filming"
        ]
    },
    {
        "Gardening": [
            "Planting Seeds",
            "Harvesting Crops",
            "Sustainable Farming",
            "Herb Gardens",
            "Organic Farming Techniques"
        ]
    },
    {
        "Space": [
            "Rocket Building",
            "Telescope Stargazing",
            "Space Simulations",
            "Astronaut Training Games",
            "Planetarium Visits"
        ]
    },
    {
        "Mythology": [
            "Role-playing Games",
            "Fantasy Storytelling",
            "Cosplay Design",
            "Mythology Quizzes",
            "Dungeon Master Workshops"
        ]
    },
    {
        "Strategy": [
            "Chess Tournaments",
            "Strategy Board Games",
            "Puzzle Challenges",
            "Escape Room Games",
            "Critical Thinking Puzzles"
        ]
    },
    {
        "Eco-Warrior ": [
            "Beach Clean-up Drives",
            "Wildlife Conservation Projects",
            "Eco-friendly Crafting",
            "Nature Hikes",
            "Sustainable Living Workshops"
        ]
    },
    {
        "Mystery": [
            "Treasure Hunts",
            "Escape Room Challenges",
            "Spy Training Games",
            "Mystery-solving Activities"
        ]
    }
]
```

Refer to the full list of categories and subcategories in the `categories_and_sub_categories` section.

---

## Contribution Guidelines

1. Follow the data extraction steps in the specified order.
2. Ensure all JSON files follow the specified structure.
3. Use valid and complete URLs for fields like `siteLink`, `logoLink`, and `profileImage`.
4. Map categories and subcategories accurately based on the provided list.
5. Provide clear and concise descriptions for all fields.
6. Submit pull requests with detailed explanations of changes.

---

Thank you for contributing to this project! If you have any questions or need further clarification, feel free to open an issue.

---

**Note:** Replace placeholders like `{categories_str}` and `{camps_and_sessions}` with actual values when creating the JSON files.



## Branching Process
To ensure smooth collaboration and maintain a clean version history, follow these steps to create and manage branches in this project:

1. Clone the Repository
Before you begin, clone the repository to your local machine:

git clone https://github.com/neelgaitech/pdf-extract-data
cd your-repository-name

2. Create a New Branch
create a new branch for your work to avoid conflicts with the main branch:

git checkout -b scrape/pdf-name


3. Code Review and Merge
After submitting the PR, the project maintainers will review your changes.
Address any feedback or requested changes.
Once approved, your branch will be merged into the main branch.