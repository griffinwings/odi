<img src="https://i.imgur.com/4Zf3O35.png" height="94">

TypeScript framework for creating enterprise-grade (web) applications with simple and minimalistic API, that allows you to focus on business logic. Based on declarative and imperative programming, inspiried by [ASP.NET](https://www.asp.net/) / [Spring](https://spring.io/). 

**Check [Docs](https://odi.gitbook.io/core) for more details.**

Odi provides feature set for creation of easy supportable and scalable web applications.

Features Overview:
 - [x] MVC
 - [x] Full-typed DI / IoT
 - [x] Authentication
 - [x] WebSockets
 - [x] TypeORM integration
 - [ ] GraphQL
 - [ ] AOP
 - [ ] SSR
 
For future updates check [Roadmap](https://github.com/Odi-ts/Odi/wiki/Roadmap)
 
## 🚀 Getting Started 
1. Install npm package<br/>
  `npm install odi --save`

2. Install reflect-metadata <br/>
	 `npm install reflect-metadata --save`
	
3. Import reflect-metadata (for example in  `index.ts`):<br/>
	 `import "reflect-metadata";`
	
4. Enabled the following settings in `tsconfig.json`
	```json
	"emitDecoratorMetadata":  true, 
	"experimentalDecorators":  true
	```

	
 ## 🌪 Example
 ```typescript
import { Controller, IController, Post, Get, Data } from 'odi';

@Controller()
export class TodoController extends IController {

    @Autowired()
    todoService: TodoService;

    @Get index() {
        return `Hello, ${this.request.ip}`;
    }

    @Post async save(toDo: TodoDTO) {
        await this.todoService.save(toDo);
    }
    
    @Get async '/:id' (id: string) {
        const todo = await this.todoService.find(id);
        
        if(!todo) 
          throw NotFound;
        
        return todo;
    }
}
 ```
