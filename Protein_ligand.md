Resíduos interagindo em docking proteína-ligante
================

### Docking

usar o servidor [ClusPro](https://cluspro.bu.edu/home.php).

carregar o arquivo .pdb da proteína e do ligante e selecionar o modo.
<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/cluspro.png" alt="ClusPro interface" width="90%" />
<p class="caption">
ClusPro interface
</p>

### RING

**1** Editar o arquivo de saída do ClusPro, modificando o nome da cadeia;

<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/alt_pdb.png" width="100%" style="display: block; margin: auto;" />

**2** Utilizar o .pdb editado como entrada no [RING](http://protein.bio.unipd.it/ring/);

<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/ring_in.png" width="60%" style="display: block; margin: auto;" />

**3** Baixar os arquivos do RING.

<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/ring_out.png" width="60%" style="display: block; margin: auto;" />

### Chimera

**1** No arquivo **edges.txt** de saída do RING, vá até as linhas que descrevem as interações do ligante que começam com **B:** na primeira coluna. A Informação da primeira(\*\*B:2:\_:GLN**) coluna indica a cadeia do .pdb(**B**), a posição do resíduo naquela cadeia(**2**) e o nome do resíduo(**GLN\*\*)

<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/edges.png" alt="Arquivo de edges do RING" width="60%" />
<p class="caption">
Arquivo de edges do RING
</p>

**2** vamos marcar as interações de ponte de hidrogênio, que começam com **HBOND:** na segunda coluna. Para isso, no Chimera, vamos selecionar todos os átomos da cadeia A(indicados na terceira coluna) que interagem com a cadeia B. No chimera, após carregar o arquivo .pdb (output editado do ClusPro), vá em **Favorites &gt; Command Line** e o painel de linha de comandos vai aparecer na parte de inferior da janela do chimera.

<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/Chimera1.png" width="80%" style="display: block; margin: auto;" />

**3** No painel de linha do comando do chimera, rode o comando para selecionar os resíduos que deseja mostrar a cadeia lateral. Após selecionar os resíduos vá em **Actions &gt; Atoms/Bonds &gt; Show**.

``` bat
select: 99,67,63,62,146,152,159,171.A
#seleciona os resíduos 99,67,63,62,146,152,159,171 da cadeia A
```

<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/Chimera2.png" width="80%" style="display: block; margin: auto;" />

repita o mesmo procedimento para os resíduos da cadeia B

``` bat
select :2,3,4,7,9,10.B
```

**4** Para marcar as interações, vá em **Tools &gt; Structure Analysis &gt; Distances** e vai aparecer a janela de seleção dos átomos.

<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/Chimera3.png" width="80%" style="display: block; margin: auto;" />

selecione os átomos para mostrar a interação e click em "Create" na janela de Distances:

``` bat
select :159.A@OH :2.B@O
#seleciona o átomo OH, do resíduo 159 da cadeia A e o elemento O do resíduo 2 da cadeia B
```

Faça o mesmo para as outras pontes de hidrogênio.

``` bat
select :171.A@OH :2.B@OE1
select :62.A@NH2 :3.B@O
select :63.A@OE1 :3.B@NZ
select :67.A@OG :3.B@NZ
select :99.A@OH :4.B@N
select :152.A@OE2 :7.B@N
select :146.A@NZ :9.B@O
select :146.A@NZ :10.B@O
```

no final, a janela de medição de distâncias vai tá assim:

<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/Chimera4.png" width="80%" style="display: block; margin: auto;" />

E o pdb mostrando as pontes.

<img src="https://raw.githubusercontent.com/diegogotex/protein_ligand/master/images/Chimera5.png" width="80%" style="display: block; margin: auto;" />
