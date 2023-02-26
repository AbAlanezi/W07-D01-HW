create database store;

create table countries(
    code int(10) primary key ,
    name varchar(20) unique ,
    continent_name varchar(20) not null
);

create table users(
    id int(10) primary key ,
    full_name varchar(20) not null ,
    email varchar(20) unique ,
    gender char(1),
    data_of_birth varchar(15) not null ,
    created_at timestamp default current_timestamp,
    country_code int(10),
    foreign key (country_code) references countries(code),
    check(GENDER in ('M', 'F'))
);

create table orders(
    id int(10) primary key ,
    user_id int(10) ,
    status varchar(6) not null ,
    created_at timestamp default current_timestamp,
    foreign key (user_id) references users(id),
    check(status in ('start', 'finish'))
);

create table order_products(
    order_id int(10),
    product_id int(10),
    quantity int(30) default (0),
    foreign key (order_id) references orders(id),
    foreign key (product_id) references products(id)
);

create table products(
    id int(10) primary key ,
    name varchar(10) not null ,
    price int(20) default (0) ,
    status  varchar(10) ,
    created_at timestamp default current_timestamp,
        check(status in ('valid', 'expired'))

);

insert into countries values (1, 'Riyadh', 'Asia');
insert into users values (1, 'AbdAlazez Alanezi', 'az@gmail.com', 'm', '2000/11/6', CURRENT_TIME(), 1);
insert into orders values (1, 1, 'start', CURRENT_TIME());
insert into products values (1, 'House', 0.0, 'valid', CURRENT_TIME());
insert into order_products values (1, 1, 10);


update  countries set  name='Dammam' where code='1';

delete from  users where id='1';

![ERdaigram](https://user-images.githubusercontent.com/123538854/221429919-b5c70df7-7231-4824-9977-45d4abc317a1.JPG)






