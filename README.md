# python-with-mysql
working on a database with the help of coding in python

import mysql.connector as connector

class DBHelper():
    def __init__(self):
        self.con = connector.connect(host='',
                                    user='',
                                    password='',
                                    port='',
                                    database='')
        query= 'create table if not exists dtaa(userId int primary key, userName varchar(45))'
        cur=self.con.cursor()
        cur.execute(query)
        print("Created")

    #insert
    def insert_user(self,userid,username):
        query= "insert into dtaa(userId,username) values ('{}','{}')".format(userid, username)
        print(query)
        cur=self.con.cursor()
        cur.execute(query)
        self.con.commit()
        print('user inserted')


    #fetch all data from database
    def fetc_all(self):
        query= 'select * from dtaa'
        cur=self.con.cursor()
        cur.execute(query)
        for row in cur:
            print("UserId : " , row[0])
            print("User Name : ",row[1])
            print()
            print()


    #deleting record
    def delete_user(self,userId):
        query='delete from dtaa where userId={}'.format(userId)
        print(query)
        c=self.con.cursor()
        c.execute(query)
        self.con.commit()
        print('deleted')


   #update database
    def update_user(self,userId,newName):
        query= "update dtaa set userName='{}' where userId={}".format(newName,userId)
        print(query)
        cur= self.con.cursor()
        cur.execute(query)
        self.con.commit()
        print("updated")


helper= DBHelper()

#insert
#helper.insert_user(1452,"viku")
# helper.insert_user(1560,"tiku")
# helper.insert_user(1454,"jitku")
# helper.insert_user(1434,"satviku")
# helper.insert_user(1417,"vikallu")
#print(helper)
#helper.delete_user(1434)
helper.update_user(1454,'Vivek Bhatia')
helper.fetc_all()






