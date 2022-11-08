# Prisma ORM Cheatsheet
Quick procedure how to setup and use prisma orm for nest project
## Installation
```
yarn add -D prisma@latest
yarn add prisma@client
```
## Setup prisma
```
npx prisma init //init prisma
npx prisma migrate dev //run after editing schema
npx prisma generate //run to generate client
```
## Setup service
```
prisma.service.ts

export class PrismaService extends PrismaClient {
    constructor(private config: ConfigService) {
        super({
            db: {
                url = config.get('DATABASE_URL')
                //you can hard coded the URL
                //use config.get to get .env variable
            }
        })
    }
}
```

## Export service (globally)
```
prima.module.ts

@Global()
@Module({
    providers: [PrismaService],
    exports: [PrismaService]
})
```

## Using the service
```
auth.service.ts

//inside a class
constructor(private prisma: PrismaService){}

async findUser(id: number) : Promise<any> {
    return await this.prisma.user.findUnique({
        ...
    })
}
```
