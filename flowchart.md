```mermaid
flowchart TB
    Start([Начало]) --> DefineTheme[Определение тематики перевода]
    DefineTheme --> DefineType[Определение типа документа]
    DefineType --> CheckResources{Проверка ресурсов}
    
    CheckResources --> |Есть| StudyResources[Изучение и применение терм.баз/стайлгайдов/ памяти переводов]
    CheckResources --> |Нет| ExtractTerms[Выделение ключевых терминов]
    StudyResources --> ExtractTerms
    
    ExtractTerms --> SendTerms[Отправка терминов на согласование]
    SendTerms --> TermsApproved{Термины согласованы?}
    
    TermsApproved --> |Да| Translation[Выполнение перевода переводчиками]
    TermsApproved --> |Нет| ExtractTerms
    
    Translation --> TechReview[Проверка техническим редактором]
    TechReview --> StyleReview[Проверка редактором-лингвистом]
    StyleReview --> Proofreading[Проверка корректором]
    
    Proofreading --> ClientReview[Отправка заказчику на согласование]
    ClientReview --> ClientApproved{Заказчик согласен?}
    
    ClientApproved --> |Нет| Corrections[Внесение исправлений]
    Corrections --> TechReview
    
    ClientApproved --> |Да| End([Завершение])
    ```