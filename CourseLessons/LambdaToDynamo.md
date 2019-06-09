https://www.youtube.com/watch?v=usgK4KsdNWM&list=PLlY4qzVu1zWul67SzrOs2WRgQfq9ejua4&index=17&t=20s  


# Create a Lambda with node.js 8.10
Lambda Code  
   
const AWS = require('aws-sdk');  
const db = new AWS.DynamoDB.DocumentClient({  
    region: 'eu-west-1'  
});  
  
exports.handler = async (event) => {  
    const params = {  
        TableName: 'DynamoDBTutorial',  
        Item: event  
    };  
    const id = '23rrefwrtrfwe';  
    params.Item.id = id;  
      
    return await db.put(params).promise();  
};  

# Create a DynamoDB Table DynamoDBTutorial  
  
# Create a IAM Policy and a IAM Role
IAM Policies  
Name the policy put-item-dynamodb-tutorial  
Edit the policy with Visual Editor  
Service: DynamoDB  
Actions: Write, select PutItem  
Resources: Select arn:aws:dynamodb:eu-west-1:839972072690:table/DynamoDBTutorial  

# Test the Lambda Function
In Execution Role, choose "Use an existing role", "dynamoDBTutorial"  
Test with a sample test event  
