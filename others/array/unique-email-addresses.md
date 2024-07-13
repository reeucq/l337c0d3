# Question

Every valid email consists of a local name and a domain name, separated by the '@' sign. Besides lowercase letters, the email may contain one or more '.' or '+'.

For example, in "alice@leetcode.com":

- "alice" is the local name
- "leetcode.com" is the domain name

## Rules for Local Name

1. **Periods (.)**

   - If you add periods '.' between some characters in the local name part of an email address, mail sent there will be forwarded to the same address without dots in the local name.
   - Note that this rule does not apply to domain names.

   Example:

   - "alice.z@leetcode.com" and "alicez@leetcode.com" forward to the same email address.

2. **Plus Sign (+)**

   - If you add a plus '+' in the local name, everything after the first plus sign will be ignored.
   - This allows certain emails to be filtered.
   - Note that this rule does not apply to domain names.

   Example:

   - "m.y+name@email.com" will be forwarded to "my@email.com".

**Note:** It is possible to use both of these rules at the same time.

Given an array of strings `emails` where we send one email to each `emails[i]`, return the number of different addresses that actually receive mails.

## Leetcode Link

[929. Unique Email Addresses](https://leetcode.com/problems/unique-email-addresses/)

## Approaches

1. **Using Set and String Operations**: We can use a set to store the unique email addresses. For each email address, we can split the email address into local name and domain name. Then we can remove the periods and ignore the characters after the first '+' sign. Finally, we can add the local name and domain name together and add it to the set. The size of the set will give us the number of unique email addresses.

1. **Using Set and String Builder**: We can use a set to store the unique email addresses. For each email address, we can iterate through each character of the email address. We can ignore the characters after the first '+' sign and remove the periods. Finally, we can add the local name and domain name together and add it to the set. The size of the set will give us the number of unique email addresses.

## Solutions

### Java Approach 1

```java
public int numUniqueEmails(String[] emails) {
        Set<String> uniqueEmails = new HashSet<>();

        for (String email : emails) {
            String[] parts = email.split("@");
            String localName = parts[0].replaceAll("\\+.*", "").replace(".", "");
            uniqueEmails.add(localName + "@" + parts[1]);
        }

        return uniqueEmails.size();
    }
```

### Java Approach 2

```java
public int numUniqueEmails(String[] emails) {
   Set<String> uniqueEmails = new HashSet<>();

   for (String email : emails) {
      StringBuilder sb = new StringBuilder();
      boolean reachedPlus = false;
      boolean reachedAt = false;

      for (char c : email.toCharArray()) {
            if (c == '@') reachedAt = true;
            if (reachedAt) sb.append(c);
            else if (!reachedPlus) {
               if (c == '+') reachedPlus = true;
               else if (c != '.') sb.append(c);
            }
      }

      uniqueEmails.add(sb.toString());
   }

   return uniqueEmails.size();
}
```
