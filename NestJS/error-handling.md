# Error Handling 
make sure the app not crashing. Use case on reading @unique value, when new user created with same email addreas, it will break
## Long form
```
try {
    //create new User
} catch (err) {
    //if error come from prisma
    if (err instanceOf PrismaClientKnownRequestError) {
        if (err.code == 'P2002') {
            throw new ForbiddenException('Credential Taken')
            //P2002 = prisma code for duplication field
        }
    }
    //if not
    throw err
}
```
## Compact form - Guard Condition
```
const user = this.prisma.user.findUnique(...)
if (!user) {
    throw new ForbiddenException('Credential incorrect')
}
```