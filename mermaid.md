erDiagram
    users ||--o{ questions : writes
    users ||--o{ answers : writes   
    users ||--|| permission : writes
	


    questions ||--o{ comments : contains


    comments ||--o{ likes 
    Comments ||--o{ reports



    users {
        int id PK
        varchar email UK "NOT NULL"
        varchar password "NOT NULL"
        varchar nickname "NOT NULL"
        varchar skin_mbti
        datetime created_at "NOT NULL"
        datetime updated_at "NOT NULL"
        datetime deleted_at
        varchar permission
        varchar level
    }


    boards {
    	int id PK
	varchar name
	varchar category FK
    }
    questions {
        int id PK
        int user_id FK “NOT NULL”
	  varchar board_id FK “NOT NULL”
        varchar category_id FK “NOT NULL”
        varchar title “NOT NULL”
        text content “NOT NULL”
        int view_count “DEFAULT 0”
        int like_count “DEFAULT 0”
        datetime created_at
        datetime updated_at
    }
    comments {
        int id PK
        int user_id FK “NOT NULL”
        int question_id FK “NOT NULL”
        text content “NOT NULL”
        int like_count “DEFAULT 0”
        datetime created_at
        datetime updated_at
    }
    likes {
        int id PK
        int user_id FK “NOT NULL”
        varchar target_type “NOT NULL”
        Int target_id “NOT NULL”
        datetime created_at
    }    
    
    Products {
    	 int id PK
	 varchar mbti FK
	 varchar name
	 varchar description
	 int price
    }
    
    permission {
	 int id PK
	 int user_id FK 
	 varchar status
	 datetime requested_at 
	 datetime resolved_at
    }
		
    report {
	 int id PK
	 int answer_id FK, “NOT NULL”
	 int question_id FK, “NOT NULL”
	 varchar status “DEFAULT PENDING”
	 varchar reason, 
	 datetime reported_at
}
	
    category {
    	 int id PK
        varchar type
    }
  
    mbti_info{
	 char code PK
	 varchar nickname
    }


    mbti_traits {
	 charletter PK,
	 tinyint axis_order,
 varchar axis_name,
 varchar label,
 varchar description,
 varchar care_point
    }

    mbti_rotuines {
	 int id PK,
 char mbti_code FK,
 enum time_of_day,
 tinyint step_order,
 varchar step,
 varchar tip
    }
	
    test_results {
 int id PK
 int user_id FK
 char mbti,
 tinyint o_score,
 tinyint s_score,
 tinyint t_score,
 tinyint e_score,
 varchar tip1,
 varchar tip2
 tinyint severe_warning,
 datetime created_at
    }

    
    test_questions {
 int id PK
 varchar text
    }


    


    purchase_reviews {
    	 INT id PK “NOT NULL”,
    	 INT user_id FK “NOT NULL”,
    	 INT product_id FK “NOT NULL”,
	 CHAR(4) mbti_code FK
    	 VARCHAR(200) title “NOT NULL”,
    	 TEXT content “NOT NULL”,
    	 VARCHAR(500) image_url “NOT NULL”,
    	 DATETIME created_at “NOT NULL”,
    	 DATETIME updated_at “NOT NULL”
    }

