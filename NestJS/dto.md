# Data Transfer Object
object that define how the data will sent over the internet
## using barrel export pattern
```
auth/dto/login.dto.ts

export class LoginDto {
    email: string
    password: string
}
```
```
auth/dto/index.ts

export * from './login.dto.ts'
```
## accesing
```
auth/auth.controller.ts

import {LoginDto} from './dto'
```

