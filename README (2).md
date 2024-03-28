
# Project Title

SOLID

Single Responsibility
Open-Closed
Liskov Substitution
Interface Segregation
Dependency Inversion




# Пример Single Responsibility
Single Responsibility у модуля должна быть только одна причина для изменения
-
class Auto {
    constructor(model: string) {}
    getCarModel() {}
    saveCustomerorder(0: Auto) {}
}

+ последущее расширения будут затрагивать конкретный класс
class Auto {
    constructor(model: string) {}
    getCarModel(){}
    getCarModel(){}
}

class CustomerAuto {
    saveCustomerorder(o: Auto){}
    getCustomerorder(id: string){}
    removeCustomerorder(id: string){}
}

class Auto {
    updateCarSet(set: object){}
}

# Пример Open-Closed
Open-Closed модуль должен быть для расширения, но закрыт для изменения

abstract class CarPrise {
    abstract getPrice(): string
}

class Tesla extends CarPrise {
    getPrice(){
        return '80 000$'
    }
}

class Audi extends CarPrise {
    getPrice(){
        return '50 000$'
    }
}

class Bmw extends CarPrise {
    getPrice(){
        return '70 000$'
    }
}

const shop: Array<CarPrise> = [
    new Tesla(),
    new Audi(),
    new Bmw(),
]
const getPrice = (auto: Array<CarPrise>): string | void => {
    for (let i = 0; i < auto.length; i++){
        aauto[i].getPrice()
    }
}

getPrice(shop)

# Пример Liskov Substitution
Liskov Substitution используем общий интерфейс

interface Figure{
    setWidth(width: number): void
    setHeight(height: number): void
    areaof(): void
}

class Rectangle implements Figure{
    setWidth(width: number): void
    setHeight(height: number): void
    areaof(): void
}

class Square implements Figure{
    setWidth(width: number): void
    setHeight(height: number): void
    areaof(): void
}


# Пример Interface Segregation
Interface Segregation сущьности не должны зависить от интерфейса, который они используют

interface TeslaSet {
    getTeslaSet(): any
}

interface AudiSet {
    getAudiSet(): any
}

interface BmwSet {
    getBmwSet(): any
}
class Tesla implements TeslaSet {
    getTeslaSet(): any {}
}

class Audi implements AudiSet {
    getAudiSet(): any {}
}

class Bmw implements BmwSet {
    getBmwSet(): any {}
}


# Пример Dependency Inversion

Dependency Inversion модули высших уровней не должны зависитьь от модулей низких уролвней оба должны зависить от обстракций не должны зависить от деталей

interface Connection {
    request(url: string, options: any): any
}

class Http {
    constructor(private httpConnection: Connection) {}

    get(url: string, options: any) {
        this.httpConnection.request(url, 'GET')
    }

    post(url: string){
        this.httpConnection.request(url, 'POST')
    }
}

class xmlHttpRequestService {
    open(){}
    send(){}
}

interface Connection {
    request(url: string, options: any): any
}

class xmlHttpService implements Connection {
    xhr = new xmlHttpRequestService()

    request(url: string, type: string) {
        this.xhr.open()
        this.xhr.send()
    }
}