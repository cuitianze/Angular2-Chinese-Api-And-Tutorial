# Angular知识清单（备忘录）

引导应用 | `import {bootstrap} from 'angular2/angular2';`
-----|-----
`bootstrap(MyAppComponent, [MyService, provide(...)]);` | 引导根组件为MyAppComponent的应用，配置依赖注入的服务

模板标签 | ``
-----|-----
`<input [value]="firstName">` | 属性value的值设为firstname
`<div [attr.role]="myAriaRole">` | 属性role的值设为myAriaRole
`<div [class.extra-sparkle]="isDelightful">` | 如果isDelightful（可为相等比较语句）为true，则添加css类名extra-sparkle。
`<div [style.width.px]="mySize">` | 将width设为mySize，单位可选
`<button (click)="readRainbow($event)">` | 点击事件触发时执行readRainbow($event)函数
`<div title="Hello {{ponyName}}">` | 属性值内插字符串，等于`<div [title]="'Hello' + ponyName">`
`<p>Hello {{ponyName}}</p>` | 文本内插字符串
`<my-cmp [(title)]="name">` | 数据双向绑定，等于`<my-cmp [title]="name" (titleChange)="name=$event">`
```<video #movieplayer ...>  <button (click)="movieplayer.play()"> </video>``` | 创建本地变量movieplayer
`<p *my-unless="myExpression">...</p>` | *号代表当前元素会被嵌入到模板中
`<p>Card No.: {{cardNumber | myCreditCardNumberFormatter}}</p>` | 过滤器
`<p>Employer: {{employer?.companyName}}</p>` | ？可处理employer为undefined的情况，如果为undefined，后面表达式将不再执行

内置指令 | `import {NgIf, ...} from 'angular2/common';`
-----|-----
`<section *ngIf="showSection">` | 根据showSection的值，删除或重新生成Dom🌲的一部分
`<li *ngFor="#item of list">` | 将li元素及其内容丢进模板中，为list中的每一个item实例化视图(上已述*号作用)
`<div [ngSwitch]="conditionExpression">   <template [ngSwitchWhen]="case1Exp">...</template>   <template ngSwitchWhen="case2LiteralString">...</template>   <template ngSwitchDefault>...</template> </div>` | 开关指令，根据当前conditionExpression的值，选择一个模板（匹配不到则默认）
`<div [ngClass]="{active: isActive, disabled: isDisabled}">` | 通过变量值的真假，控制css类名的开关

Form表单 | `import {FORM_DIRECTIVES} from 'angular2/common';`
-----|-----
`<input [(ngModel)]="userName">` | 提供数据双向绑定，解析和验证

Class decorators（类的修饰器，语法糖）| `import {Directive, ...} from 'angular2/core';`
-----|-----
@Component({...}) class MyComponent() {} | 声明一个组件类，并提供元数据
@Pipe({...}) class MyPipe() {} | 声明一个pipe类，并提供元数据
@Injectable() class MyService() {} | 声明一个有依赖的类
