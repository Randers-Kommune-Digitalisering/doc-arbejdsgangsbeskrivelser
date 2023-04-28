# TO BE FORSLAG
## Find borgere uden tidligere bevillinger

flowchart TD

subgraph Hent nye ansøgninger
    A[Søg sager ud fra Skabelon]-->
    B{Sag åben eller lukket?} 
end

subgraph Hent sagspart
    C[Hent ID]
end

subgraph Hent bevillingsbreve
    D[Søg dokumenter ud fra Skabeloner]
end

subgraph Beslutningsstøtte
    S(Overblik over borgere)
end

B --x|Lukket|H
B -->|Åben| C
C --> D
D -->|Afslag eller igen breve sendt| S
D --x|Bevilling sendt|H

H(stop)
