# Argon2 Password Hashing
## installation
```
yarn add argon2
```
## using it
```
import * as argon from 'argon2'

export class AuthService {
    async signup({dto: UserDto}) {
        //hash the password
        const hash = await argon.hash(dto.password)
        //save to db
        const user = await this.prisma.user.create({
            data: {
                email: dto.email
                hash
            },
            select: { //select field that want to be return
                id: true,
                email: true
            }
        })

        //dirty solution without select
        //delete user.hash

        return user
    }
}
```

