# Backend Server Technical Specs

## Business Goal

A language learning school wants to build a prototype of a learning portal which will act as three things:
- Iventory of possible vocabulary that can be learned
- Act as a learning record store (LRS), providing correct and wrong score on practice vocabulary
- A unified lauchpad to launch different learning apps

## Technical Requirements

- The backend will be build using Go
- The database will be SQLite3
- The API will be built using Gin
- There will be no authentication or authorization
- Everything will be treated as a single user 

## Database Schema

We have the following tables;
- words - stored vocabulary worfd
    - id integer
    - japanese string
    - romanji string
    - english string
    - parts json
- word_groups - join table for words and gprups many-to-many
    - id integer
    - word_id integer
    - group_id integer
- groups - thematic group of words
    - id integer
    - name string
- study_sessions - records of study sessions grouping word_review_items
    - id integer
    - study_session_id integer
    - group_id integer
    - created_at datetime
- word_review_items - a record of word practice, determining if the word was correct or not
    - word_id integer
    - study_session_id integer
    - corrected boolean
    - corrected_at datetime

### API Endpoints
- GET /api/dashboard/last_study_session
- GET /api/dashboard/study_progress
- GET /api/dashboard/quick_stats
- GET /api/study_activities/:id
- GET /api/study_activities/:id/study_sessions
- POST /api/study_activities/
    - required params:group_id, study_activity_id
- GET /api/words
    - pagination wirh 100 items per page
- GET /api/words_id
- GET /api/groups
    - pagination wirh 100 items per page
- GET /api/groups/:id
- GET /api/groups/:id/words
- GET /api/groups/:id/study_sessions
- GET /api/study_sessions
    - pagination wirh 100 items per page
- GET /api/study_sessions/:id
- GET /api/study_sessions/:id/words
- POST /api/reset_history
- POST /api/full_reset
- POST /api/study_sessions/:id/words/:word_id/review
    - required params: correctkkkk



