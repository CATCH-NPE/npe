classDiagram
direction BT
class application_form {
   datetime(6) created_at
   bigint member_id
   bigint recruit_id
   datetime(6) updated_at
   mediumtext content
   bigint id
}
class email_send_group {
   varchar(30) code
   varchar(100) description
   varchar(100) template_name
   datetime(6) created_at
   datetime(6) updated_at
   bigint id
}
class jectalk {
   datetime(6) created_at
   datetime(6) updated_at
   varchar(50) name
   varchar(2083) image_url
   varchar(2083) youtube_url
   varchar(255) summary
   bigint id
}
class member {
   datetime(6) created_at
   datetime(6) updated_at
   varchar(12) phone_number
   varchar(20) name
   varchar(30) email
   varchar(255) pin
   varchar(45) job_family
   varchar(10) role
   bigint semester_id
   bigint id
}
class mini_study {
   datetime(6) created_at
   datetime(6) updated_at
   varchar(50) name
   varchar(2083) image_url
   varchar(2083) link_url
   varchar(255) summary
   bigint id
}
class portfolio {
   bigint application_form_id
   datetime(6) created_at
   bigint file_size
   datetime(6) updated_at
   varchar(2083) file_url
   varchar(255) file_name
   int sequence
   bigint id
}
class project {
   date end_date
   date start_date
   datetime(6) created_at
   bigint team_id
   datetime(6) updated_at
   varchar(100) name
   varchar(100) summary
   varchar(2083) service_url
   varchar(2083) thumbnail_url
   text description
   varchar(255) tech_stack
   varchar(30) category
   bigint semester_id
   bigint id
}
class project_intro {
   int sequence
   datetime(6) created_at
   bigint project_id
   datetime(6) updated_at
   varchar(2083) image_url
   varchar(30) category
   bigint id
}
class question {
   datetime(6) created_at
   bigint recruit_id
   datetime(6) updated_at
   varchar(100) title
   varchar(255) label
   varchar(255) input_hint
   varchar(10) input_type
   tinyint(1) is_required
   int max_text_length
   int sequence
   int max_file_size
   varchar(255) select_options
   bigint id
}
class recruit {
   datetime(6) end_date
   datetime(6) start_date
   datetime(6) created_at
   datetime(6) updated_at
   varchar(45) job_family
   bigint semester_id
   bigint id
}
class review {
   datetime(6) created_at
   datetime(6) updated_at
   varchar(2083) link_url
   varchar(255) description
   varchar(255) summary
   varchar(255) title
   bigint id
}
class semester {
   varchar(20) semester_name
   tinyint(1) is_recruiting
   datetime(6) created_at
   datetime(6) updated_at
   bigint id
}
class team {
   datetime(6) created_at
   datetime(6) updated_at
   varchar(30) name
   bigint id
}
class team_member {
   datetime(6) created_at
   bigint member_id
   bigint team_id
   datetime(6) updated_at
   bigint id
}

application_form  -->  member : member_id:id
application_form  -->  recruit : recruit_id:id
member  -->  semester : semester_id:id
portfolio  -->  application_form : application_form_id:id
project  -->  semester : semester_id:id
project  -->  team : team_id:id
project_intro  -->  project : project_id:id
question  -->  recruit : recruit_id:id
recruit  -->  semester : semester_id:id
team_member  -->  member : member_id:id
team_member  -->  team : team_id:id
