# VPC-Peering

Basically here i created two VPC ,test-vpc and prod-vpc . 

## Steps 
1 .  Created a VPC named test and CIDR range is 10.0.0.0/16 . 


<img width="1280" alt="Screenshot 2024-01-03 111829" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/9ae176a3-7070-4cc2-8fc4-852b7bc94f40">



2 . Created a public subnet in test VPC with CIDR range 10.0.0.0/24

<img width="1275" alt="Screenshot 2024-01-03 111932" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/3be91c92-f444-4d39-8cc0-e205f81d8b4e">


3 . Created an EC2 instance in the test VPC using test-public-subnet . 


<img width="1280" alt="Screenshot 2024-01-03 112035" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/bcd9ae0b-b862-43fc-b050-35648d541f29">


4 . Tried to connect the EC2 instance but i get an error . This happened as the EC2 instance is in an isolated VPC . 

<img width="1280" alt="Screenshot 2024-01-03 112146" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/855a2c85-d421-4858-ad13-4b49e155d5f3">

5 . Then created an internet gateway(test-igw) and attached the internet gateway to the test VPC . 

<img width="1279" alt="Screenshot 2024-01-03 112222" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/405a0248-cb42-4d15-9326-55923f3b34a1">

<img width="1279" alt="Screenshot 2024-01-03 112249" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/007adbad-ecd5-4526-ae31-25f42adc7852">

6 . Created a route table . Here i associated the test-public-subnet and then created a route for destination 0.0.0.0/0 and target test-igw gateway . 

<img width="1280" alt="Screenshot 2024-01-03 112322" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/d8ea3547-af4f-4112-988c-55d59bf9adfb">

<img width="1280" alt="Screenshot 2024-01-03 112347" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/5c7592a0-7908-47cf-b23c-c5b71fbf2a10">

<img width="1280" alt="Screenshot 2024-01-03 112424" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/05dec320-563e-4e3d-be4f-fe865df18a8c">


7 . After this i successfully connected the EC2 instance . 

<img width="1280" alt="Screenshot 2024-01-03 112454" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/e2eed764-af45-4736-a52f-1679c09ff734">

8 . Like the above steps i created another VPC (prod-VPC) , public subnet , internet gateway and route table . 


<img width="1280" alt="Screenshot 2024-01-03 112843" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/84724296-7af2-4753-96f7-39aa494aabc2">

<img width="1280" alt="Screenshot 2024-01-03 112938" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/21f2745b-5157-4e4d-b7b2-ad60181452a0">




<img width="1280" alt="Screenshot 2024-01-03 113030" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/a821e453-f078-4099-8057-f2b79114bd4a">

<img width="1280" alt="Screenshot 2024-01-03 113158" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/c40a644b-4221-4d0a-b110-8e49d8db03b5">










<img width="1280" alt="Screenshot 2024-01-03 113215" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/b7d40bd5-bab8-4516-97ec-9932a8911ca4">



<img width="1280" alt="Screenshot 2024-01-03 113337" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/f0268f79-f300-49fa-a602-28d814cb1a8d">



<img width="1280" alt="Screenshot 2024-01-03 113432" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/81459c38-fc5d-49e8-9f8d-920e4cf3d71c">





<img width="1280" alt="Screenshot 2024-01-03 113934" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/4b8cae40-081e-4d7e-ad8f-71df0e875e9f">

9 . Then connected the EC2 instance created in the prod VPC .



<img width="1280" alt="Screenshot 2024-01-03 114546" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/10019f57-8775-4384-9147-1d5f63fb6404">


10 . Now to establish connection between test VPC and prod VPC , i have created a peering connections(test-prod-peering) . Here requester VPC is test-VPC and accepter VPC is the prod-VPC .

<img width="1280" alt="Screenshot 2024-01-03 114716" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/9349f623-3530-4fd4-bbd6-4b2eb8062e93">


11 . Then accepted request . 

<img width="1280" alt="Screenshot 2024-01-03 114742" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/2ea2bc99-c4fc-4106-bd1d-b1296d296e40">

12 . Now created a route in test-route-table where target destination is CIDR range of prod-VPC (192.168.0.0/16) . 


<img width="1280" alt="Screenshot 2024-01-03 114906" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/e912d429-9b3b-4178-a9ba-2433b4a2839e">


13 . Like the above step created a route in prod-route-table where target destination is CIDR range of test-VPC (10.0.0.0/16) .


<img width="1279" alt="Screenshot 2024-01-03 115001" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/9baad815-da42-4853-aa59-2ec7f008bf94">

14 .  To check whether both the VPC are connecting or not we have to use PING command . But to do this ping command , ICMP protocol is needed . So added ICMP protocol in both the security group of EC2 instances .


<img width="1280" alt="Screenshot 2024-01-03 115132" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/6c8d386d-352f-42a8-a6e4-28b4d2cc2356">

<img width="1279" alt="Screenshot 2024-01-03 115220" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/61c5758c-cf25-4030-9556-fd4a706525f6">

15 . After i used ping command in both the EC2 instance to check whether the two VPC are connecting or not . 

<img width="1279" alt="Screenshot 2024-01-03 115310" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/46190532-d442-42de-bed2-cd47e561f934">

<img width="1280" alt="Screenshot 2024-01-03 115351" src="https://github.com/PranitRout07/VPC-Peering/assets/102309095/d773f753-f931-4e79-9d87-caac5d37b16c">
