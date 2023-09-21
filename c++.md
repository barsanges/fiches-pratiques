# C++

## GDB

`break src/foo/bar.cpp:273` : ajoute un point d'arrêt à la ligne 273
de bar.cpp

`catch throw` : arrête l'exécution lorsqu'une exception est lancée

`catch catch` : arrête l'exécution lorsqu'une exception est récupérée

`condition BNUM COND` : ne s'arrête au point d'arrêt n°BNUM que si la
condition COND est vraie

`n (next)` : exécute la ligne suivante

`c (continue)` : exécute le programme jusqu'au prochain point d'arrêt

`s (step)` : exécute la ligne immédiatement suivante dans l'ordre
d'exécution (i.e. : rentre dans les fonctions)

`p (print) foo` : affiche foo
  * `p foo.operator()(0, 0)` : affiche foo(0, 0) (par exemple si foo
    est un tableau Eigen)
  * `p (char *)foo->getObjectID()` : affiche la string renvoyée par
    getObjectID

`k (kill)` : stoppe le programme en cours d'exécution

`l (list)` : affiche le code autour de la ligne courante

`info breakpoints` : affiche la liste de tous les points d'arrêt
(breakpoints, watchpoints et catchpoints)

`disable BNUM` : désactive le point d'arrêt n°BNUM

`d (delete) BNUM` : supprime le point d'arrêt n°BNUM

`r (run) ARGS` : lance le programme avec les arguments de ligne de
commande ARGS, par exemple :

    run --license=EMRLIB_license.txt -t 1 INPUTS_*

`bt (backtrace)` : affiche le trace back

`frame n` : sélectionne la frame n du trace back

`shell cmd` : exécute la commande bash cmd (par exemple : `shell ls`)

## gprof

    g++ ... -pg # Concerne à la fois le compilateur et le linker
    EXECUTABLE PROGRAM_PARAMETER ... PROGRAM_PARAMETER # Crée un fichier gmon.out, en plus de l'exécution normale
    gprof OPTIONS EXECUTABLE gmon.out > OUTFILE
    gprof2dot OUTFILE | dot -Tpdf -o output.pdf

gprof ne fonctionne pas avec les librairies dynamiques.

## Valgrind

### Profiling

    valgrind --tool=callgrind EXECUTABLE PROGRAM_PARAMETER ... PROGRAM_PARAMETER 2>&1 | tee callgrindresults.txt
    gprof2dot OUTFILE -f callgrind | dot -Tpdf -o output.pdf
    qcachegrind callgrind.out

### Fuites mémoires

    valgrind --tool=helgrind EXECUTABLE PROGRAM_PARAMETER ... PROGRAM_PARAMETER 2>&1 | tee helgrindresults.txt
