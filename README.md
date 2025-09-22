# aws-identity-and-access-management

A deep dive into AWS IAM (Identity and Access Management), focusing on
creating and managing users, groups, and roles. This project
demonstrates how to implement policies to secure AWS resources, ensuring
proper access control and enhancing overall cloud security.

## Granting Access to Users and Entities

### Creating a Policy

We begin by creating a policy granting full access to EC2 instances and
then attaching it to a user named Eric.

1.  Navigate to the AWS Management Console and search for 'IAM'.\
    ![IAM](iam.png)

2.  On the IAM dashboard, navigate to the left pane and click on
    'Policies'. Use the search bar to type 'ec2' and select
    **AmazonEC2FullAccess** from the list of policies. Then click on
    **Create policy** at the top right corner.\
    ![EC2 Policy](ec2-full-access.png)

    In the 'Service' dropdown, select **EC2** and check the box for
    **All EC2 actions (ec2\*)**.\
    ![All EC2 Actions](all-ec2-actions.png)

    Scroll to the bottom, tick **All** under resources, and click
    **Next**.\
    ![All Resources](all-resources.png)

    On the Review and Create page, enter a name for the policy
    (`ec2-full-access`) and a description, then click **Create
    policy**.\
    ![Policy Name](policy-name.png)

### Creating User Eric

On the left pane, click **Users**, then click **Create user** at the top
right.\
![New User](new-user.png)

Enter a user name (`eric`) and check the box for *Provide user access to
the AWS Management Console - optional*.

Select *I want to create an IAM user* and choose **Custom password**.
Enter a password, check *Users must create a new password at next
sign-in - Recommended*, then click **Next**.\
![User Details](user-details.png)

Select **Attach policies directly**, choose the `ec2-full-access` policy
created earlier, then click **Next**.\
![Attach Policy](attach-policy.png)

Review the details and click **Create user**.\
![Create User](create-user.png)

On the review page, notice the difference between **Customer managed**,
**AWS managed**, and **inline** policies.

The new user `eric` has been created successfully. Save his sign-in
details securely for future use, then click **Return to users list**.\
![User Created Successfully](user-created-successfully.png)

### Creating User Group

On the left pane, click **User groups** and then click **Create
group**.\
![New Group](new-group.png)

Enter a group name (`Backend-Developers`) and click **Create user
group**.\
![Group Created](group-created.png)

### Creating User Jack and Adding Him to the Group

Click **Users**, then **Create user**. Enter `jack` in the user name
field and click **Next**.\
![User Details](user-jack-details.png)

In the 'Permissions options' section, select **Add user to group**,
check the `Backend-Developers` group, and click **Next**.\
![User Permissions](user-jack-permissions.png)

Review the details for Jack and click **Create user**.\
![User Jack Created successfully](jack-created-successfully.png)

### Creating User Ade and Adding Him to the Group

Repeat the process to create a user named `Ade` and add him to the
`Backend-Developers` group.\
![User Ade Created Successfully](user-ade-created-successfully.png)

### Creating Backend-Developers Policy

Now, create a new policy for the `Backend-Developers` group. Navigate to
**Policies** and click **Create policy**.\
![New Policy](new-policy.png)

On the 'Specify permissions' page, select **EC2** as the service.\
![Service Selection](ec2-service.png)

Click **Add more permissions** and select **S3**. Check **All EC2
actions (ec2\*)** and **All S3 actions (s3\*)**. Select **All** under
resources and click **Next**.\
![Policy Permissions](policy-permissions.png)

Enter a name (`backend-developers-policy`) and a description, then click
**Create policy**.\
![Create Policy](backend-policy.png)

### Attaching Policy to User Group

From the left pane, click **User groups**, then select the
`Backend-Developers` group.\
![Selecting User Group](select-usergroup.png)

Go to the **Permissions** tab, click **Add permissions**, and choose
**Attach policies**.\
![Permissions Tab](permissions-tab.png)

Search for the `backend-developers-policy`, select it, and click
**Attach policies**.\
![Attach Policy to Group](group-attach-policy.png)

The policy has now been successfully attached to the group, granting
full access to EC2 and S3 for all group members.\
![Policy Successfully Attached](group-attach-successful.png)

------------------------------------------------------------------------

## Project Reflection

-   **Understanding IAM**: IAM serves as the security foundation for AWS
    resources, controlling access and permissions.\
-   **Security Importance**: IAM ensures data protection, compliance,
    and prevents unauthorized access.\
-   **Policy Creation**: Crafting IAM policies helps regulate resource
    access effectively.\
-   **Practical Application**: Hands-on exercises provided real-world
    experience in setting up IAM users, groups, and policies, enhancing
    confidence in IAM implementation.

------------------------------------------------------------------------

## Conclusion

This project provided a comprehensive, practical understanding of AWS
IAM. By creating users, groups, and custom policies, and attaching them
appropriately, we demonstrated how to establish fine-grained access
control for AWS resources. IAM not only safeguards cloud environments
but also enables scalability and collaboration by ensuring that the
right people and teams have the right level of access. The skills
developed here form a solid foundation for managing security in
real-world AWS deployments.
