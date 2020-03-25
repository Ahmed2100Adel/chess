# chess
The 8-Queens problem in chess is to place 8 queens on a chess board such that none of the queens is threatening any of the others. A chess board is an 8 x 8 matrix of squares and queens may move any direction along a row, column or diagonal. The problem is to input the 8 columns of the queens on the rows of a chess board, with 1 being the first column and 8 being the last, e.g. 1 2 3 4 5 6 7 8 means the queens are along the diagonal, which would not be a valid solution.  Example 1:  Enter board configuration: 3 5 2 8 1 7 4 6 This is a valid configuration.  Example 2: Enter board configuration: 1 8 2 5 3 7 4 6 This is NOT a valid configuration.
Hi I'm learning matlab
 %chess
clear
clc
pos=input("please enter your positions of queens");

%create zero array
arr=zeros(8,8);

%inserting values to zero array
for i=1:8
    arr(i,pos(i))=1;
end

threatenOrNot=0;


%making sure there is no duplicate numbers
for i=1:8
    for j=i+1:8
        if pos(i)==pos(j)
            threatenOrNot=1;
            
            break;
        end
    end 
    if threatenOrNot==1
        break;
    end
end


if threatenOrNot==0
    for i=1:7
        col=pos(i);
        
        %checkin if there is diagnol or right
        m=i+1;
        for c=(col+1):8
            
            if m==8
                break
            end
            if arr(m,c)==1
                threatenOrNot=1;
                break;
            else
                 m=m+1;

            end
        end

        if threatenOrNot==1
            break;
        end
        
        
         m=i+1;
        for c=(col-1):-1:1
            if m==8
                break
            end
            if arr(m,c)==1
                threatenOrNot=1;
                break;
            else
                 m=m+1;

            end
        end
        if threatenOrNot==1
            break;
        end
    end
end
if threatenOrNot==0
    disp("This is a valid configuration.");
else
    disp("This is NOT a valid configuration.");
end

