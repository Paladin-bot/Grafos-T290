# Grafos-T290
Repositório destinado a armazenar os trabalhos da disciplina de Grafos da Universidade de Fortaleza (UNIFOR)

# Google Colaboratory

[Colaboratory](https://colab.research.google.com) is a research project created
to help disseminate machine learning education and research. It’s a Jupyter
notebook environment that requires no setup to use. For more information, see
our [FAQ](https://research.google.com/colaboratory/faq.html).

This repository contains the code for the Python libraries available in the
Colab.

# Teoremas para grafos hamiltonianos: 


```python
"""Teorema de Dirac:"""

def dirac(self):
    for i in self.get_vertices():
        if (not len(self.get_vertices()) >= 3 or len(self.graph[i]) < (len(self.get_vertices()))/2):
            return False
    return True

```

```python
"""Teorema de Ore:"""

def ore(self):
    count_not_adj = 0
    count_ore = 0
    for i in self.get_vertices():
        for j in self.get_vertices():
            if (i != j and not self.graph[i].__contains__(j)):
                count_not_adj = count_not_adj + 1
                if(len(self.graph[i]) + len(self.graph[j]) >= len(self.get_vertices())):
                    count_ore = count_ore + 1
    if (count_ore == count_not_adj):
        return 1
    else:
        return 0

```

```python
"""Teorema de Bondy Chvatal:"""


def bondy_chvatal(self):
  #to do instanciar o fecho com os nós:
  fecho_g = {}
  grau_g = {}
  for i in self.get_vertices():
    fecho_g[i] = []
    grau_g[i] = []
    for k in self.graph[i]:
      fecho_g[i].append(k)
      grau_g[i] = len(fecho_g[i])
  while(is_done_not_adj(fecho_g)):
    for i in self.get_vertices():
      for j in self.get_vertices():
        if(i != j and not fecho_g[i].__contains__(j) and len(fecho_g[i]) + len(fecho_g[j]) >= len(list(fecho_g.keys()))):
          fecho_g[i].append(j)
          fecho_g[j].append(i)
  index = 0;
  for i in list(fecho_g.keys()):
    if len(fecho_g[i]) == len(list(fecho_g.keys())) -1:
      index = index + 1
  if index == len(list(fecho_g.keys())):
    return 1
  else: 
    return 0

```

```python
"""Condicional de Não Adjacência:"""


def is_done_not_adj(fecho_g):
  #Ver a não adjacencia de todos os vertices
  #Dai calcular se tem alguma soma que é maior ou igual a n dado dois vertices quaisquer;
  for i in list(fecho_g.keys()):
    for j in list(fecho_g.keys()):
      if(i != j):
        if((not fecho_g[i].__contains__(j)) and len(fecho_g[i]) + len(fecho_g[j]) >= len(list(fecho_g.keys()))):
          return 1
  return 0

```

