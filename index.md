[TOC]

# Eng. de dados

Estes desafios são para testar sua habilidade técnicas, a maior parte dos desafios são extraídos do HackerRank, no final o que queremos é um arquivo com os scripts dos desafios, não tenha medo de errar, errar faz parte da sua evolução. Boa Sorte!

## Desafio SQL, fique a vontade para usar a linguagem SQL de sua preferência.

### 15 Days of Learning SQL

```mysql
select submission_date, 
(select count(distinct hacker_id)  
    from submissions as sub  
    where sub.submission_date = s.submission_date 
    and (select count(distinct sub2.submission_date) 
            from submissions as sub2 
            where sub2.hacker_id = sub.hacker_id 
            and sub2.submission_date < s.submission_date) = 
            datediff(s.submission_date , '2016-03-01')),
(select hacker_id  
    from submissions as sub 
    where sub.submission_date = s.submission_date 
    group by hacker_id 
    order by count(submission_id) desc , hacker_id limit 1) as aux,
(select name 
    from hackers where hacker_id = aux)
from (select distinct submission_date
        from submissions) as s
group by submission_date
```

### Top COmpetitors

```mysql
select hack.hacker_id, hack.name
from hackers as hack join submissions as sub
on hack.hacker_id = sub.hacker_id 
join challenges as cll 
on sub.challenge_id = cll.challenge_id
join difficulty as df 
on cll.difficulty_level = df.difficulty_level
where sub.score = df.score
group by hack.hacker_id, hack.name
having count(sub.hacker_id) > 1
order by count(sub.hacker_id) desc, sub.hacker_id asc;
```

------

##  Estrutura de Dados

### Print in Reverse

```python
def reversePrint(head):
	if head == None:
        return
    reversePrint(head.next)
    print(head.data)
```

### Maximum Element

```python
num_q = int(input())
stack=[]
for i in range(num_q):
    query=list(map(int,input().split()))
    type_q=query[0]
    if type_q==1:
        if stack:
            stack.append(max(stack[-1],query[1]))
        else:
            stack.append(query[1])
    elif type_q==2:
        stack.pop()
    else:
        print(stack[-1])
```

------

## Desafio Python

### Validating Postal Codes

```python
regex_integer_in_range = r"^[1-9]\d{5}$"
regex_alternating_repetitive_digit_pair = r"(?=(\d)\d\1)"
```

### Write a function

```python
def is_leap(year):
    leap = False
    if not(year % 4):
        leap=True
        if not(year % 100):
            leap=False
            if not(year % 400):
                leap=True
    return leap
```

### String Split and Join

```python
def split_and_join(line):
    return "-".join(line.split(" "))
```

### List Comprehensions

```python
print([[X, Y, Z] for X in range(x+1) for Y in range(y+1) for Z in range(z+1) if X + Y + Z != n])
```

------

## Desafio Eng. de Dados

A empresa de marketing ZYZ está em busca de entender o comportamento dos usuários nas redes sociais, com isso surgiu a necessidade de criar uma análise de sentimento no Twitter. Você como engenheiro de dados precisa montar uma estratégia de coleta de dados de tweets para que posteriormente os analistas possam prosseguir com o projeto.

### Escopo do projeto

- Definir o [método de coleta](m%C3%A9todo%20de%20coleta.md)

- Decidir a melhor forma de [armazenar os tweets](armazenar%20os%20tweets.md)

- Definir a infraestrutura a ser utilizada

- Definir o Pipeline de dados

A entrega é o desenho do fluxo de coleto com as ferramentas que serão utilizadas e com suas conclusões sobre a infraestrutura

  1. Por que você decidiu utilizar esta infraestrutura?
  2. Quais benefícios?
  3. Quais pontos de melhorias?
  4. É uma infraestrutura escalável?