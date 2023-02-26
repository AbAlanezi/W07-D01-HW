# W07-D01-HW

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
    gender char(10),
    data_of_birth varchar(15) not null ,
    created_at datetime,
    country_code int(10),
    foreign key (country_code) references countries(code),
    check(GENDER in ('Male', 'Female'))
);

create table orders(
    id int(10) primary key ,
    user_id int(10) ,
    status varchar(6) not null ,
    created_at datetime,
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
    created_at datetime,
        check(status in ('valid', 'expired'))

);

insert  into countries values  (1,'Riyadh','Asia');
insert  into users  values  (1,'Abdalazez','az@gmail.com','M','2000/11/6', '2022/2/1',71312);
insert  into orders  values  (3,2,'start','2023/1/2');
insert  into products  values  (5,'tool',70,'expired','2023/1/3');
insert  into order_products  values  (3,5,2);

update  countries set  name='Dammam' where code='1';

delete from  users where id='1';





