# Pipes
use case for transform and validate request
## Built in pipe
```
request body = {name: 'tara', age: '13'}

checkAge(@Body('age', ParseIntPipe) age: int) {
    return age >= 17
}
```
## Global class validation
use case for dto validation
### installation
```
yarn add class-validator class-transform
```
### setup
```
app.ts

app.useGlobalPipes(new ValidationPipe({
    whitelist: true //to filter unwanted field
}))
```
```
user.dto.ts

import {IsEmail, IsNotEmpty, IsNumber} from 'class-validation'
export class UserDto {
    @IsEmail()
    @IsNotEmpty()
    email: string

    @IsInt()
    nim: number
}

