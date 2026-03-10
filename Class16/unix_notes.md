## Basic Unix

Some important file system commands include

pwd: Print Working Directory
ls: List files and folder
cd: Chnage Directory
mkdir: Make a new Directory
rm: Delete files and Directories (!!!NO RECOVERY!!!)
nan0: A very basic text editor that is always available
less: Tow view / read text files by page (pager program)

My AWS instance:
ssh -i ~/Downloads/bimm143_ga.pem ubuntu@ec2-35-94-40-199.us-west-2.compute.amazonaws.com

To copy from my AWS instance:
scp -i ~/Downloads/bimm143_ga.pem ubuntu@ec2-35-94-40-199.us-west-2.compute.amazonaws.com ~/work/results.tsv .

## Restaring instance
 scp -i ~/Downloads/bimm143_ga.pem ubuntu@ec2-54-244-204-188.us-west-2.compute.amazonaws.com:~/work/results.tsv .