# Exporting Module
Use case for accesing other module's services
## basic export
```
prisma.module.ts

@module({
    export: [PrismaService]
})
```
accesing
```
user.module.ts

@module({
    import: [PrismaModule]
})
```
```
user.service.ts

constructor({private prisma: PrismaService}){}
```

## global export - @Global()
```
prisma.module.ts

@Global()
@module({
    export: [PrismaService]
})
```
service are available globally so no need to import the module
```
prisma.service.ts

constructor(private prisma:PrismaService){}