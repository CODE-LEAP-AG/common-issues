# got undefined type even if we defined the type already

When we have circular dependency between io-ts validator files, we will get undefined type even if we defined the type already
Eg: in `job_validator.ts` has a `CountDataResult` type and it's used in `job_validator.ts` and `user_validator.ts`

    - company_validator.ts --> import user_validator.ts
    - user_validator.ts --> import job_validator.ts
    - job_validator.ts --> import company_validator.ts

Solution: move `CountDataResult` type to a new file