---
title: A. Příklady
ms.date: 01/18/2019
ms.assetid: c0f6192f-a205-449b-b84c-cb30dbcc8b8f
ms.openlocfilehash: 061490d34829175bfbdcd84d6208aa396bb19671
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362969"
---
# <a name="a-examples"></a>A. Příklady

Následují příklady konstrukce definované v tomto dokumentu. Příkaz následující direktivy je složený pouze v případě potřeby a bez složeného příkazu odsazeno z směrnice před.

## <a name="a1-a-simple-loop-in-parallel"></a>A.1 jednoduché smyčky A paralelní

Následující příklad ukazuje, jak paralelní smyčky pomocí [paralelní pro](2-directives.md#251-parallel-for-construct) směrnice. Iterační proměnná smyčky je ve výchozím nastavení, privátní, takže není nutné explicitně zadat v klauzuli privátní.

```cpp
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```

## <a name="a2-conditional-compilation"></a>A.2 podmíněné kompilace

Následující příklady ilustrují použití podmíněné kompilace OpenMP – makro [_OPENMP](2-directives.md#22-conditional-compilation). S OpenMP kompilace `_OPENMP` stane definice makra.

```cpp
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

Defined – operátor preprocesoru umožňuje více než jedno makro má být testována v jedné – direktiva.

```cpp
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

## <a name="a3-parallel-regions"></a>A.3 paralelních oblastí

[Paralelní](2-directives.md#23-parallel-construct) – direktiva je možné v paralelních programů hrubý intervalem. V následujícím příkladu, každé vlákno v paralelní oblasti určuje, jaká část globální pole `x` pracovat na, závisí na počtu vláken:

```cpp
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```

## <a name="a4-the-nowait-clause"></a>A.4 klauzule nowait

Pokud existuje mnoho nezávislé smyčky v rámci paralelní oblasti, můžete použít [nowait](2-directives.md#241-for-construct) klauzule, aby implicitní odbourejte překážky bránící na konci `for` směrnice, následujícím způsobem:

```cpp
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```

## <a name="a5-the-critical-directive"></a>A.5 direktivy critical

Následující příklad obsahuje několik [kritické](2-directives.md#262-critical-construct) direktivy. Tento příklad znázorňuje modelu služby Řízení front, ve kterém je úkol vyřazených z fronty a pracovali. Pro ochranu proti několika vlákny vyřazování z fronty, stejný úkol, zrušení fronty operace musí být v `critical` oddílu. Vzhledem k tomu, že dvě fronty v tomto příkladu jsou nezávislé, že jsou chráněné pomocí `critical` direktivy s různými názvy, *xaxis* a *osa yrozsah*.

```cpp
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```

## <a name="a6-the-lastprivate-clause"></a>A.6 klauzule lastprivate

Někdy správné spuštění závisí na hodnotě, který proměnné přiřazuje poslední iteraci smyčky. Takové programy musí uvést všechny tyto proměnné jako argumenty [lastprivate](2-directives.md#2723-lastprivate) klauzule tak, že hodnoty proměnné jsou stejné jako při provedení smyčky je postupně.

```cpp
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

V předchozím příkladu, hodnota `i` na konci paralelní oblast vyrovná `n-1`, jako v případě sekvenční.

## <a name="a7-the-reduction-clause"></a>A.7 v klauzuli reduction

Následující příklad ukazuje, [snížení](2-directives.md#2726-reduction) klauzule:

```cpp
#pragma omp parallel for private(i) shared(x, y, n) \
                         reduction(+: a, b)
    for (i=0; i<n; i++) {
        a = a + x[i];
        b = b + y[i];
    }
```

## <a name="a8-parallel-sections"></a>A.8 paralelních oddílů

V následujícím příkladu (pro [části 2.4.2](2-directives.md#242-sections-construct)), funkce *xaxis*, *osa yrozsah*, a *zaxis* mohou být provedeny souběžně. První `section` direktiva je volitelné.  Všechny `section` direktivy, musí se zobrazit v lexikálním rozsahu `parallel sections` vytvořit.

```cpp
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```

## <a name="a9-single-directives"></a>A.9 direktiv Single

Následující příklad ukazuje, [jeden](2-directives.md#243-single-construct) – direktiva. V tomto příkladu pouze jedno vlákno (obvykle první vlákno, které nalezne `single` – direktiva) zobrazí zpráva o průběhu. Uživatel nesmí jakkoli jak pro vlákno, které se spustí `single` oddílu. Přeskočí všechny ostatní vlákna `single` části a zastavit bariéře na konci `single` vytvořit. Pokud se ostatní vlákna bez čekání na vlákno prováděno Přejít `single` části `nowait` klauzule můžete nastavit na `single` – direktiva.

```cpp
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```

## <a name="a10-sequential-ordering"></a>A.10 sekvenčního řazení

[Seřazené oddíly](2-directives.md#266-ordered-construct) jsou užitečné pro sekvenční řazení výstup z práce, která se má provést paralelně. Následující program vytiskne indexy v postupném pořadí:

```cpp
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```

## <a name="a11-a-fixed-number-of-threads"></a>A.11 A pevně daný počet vláken

Některé programy spoléhají na pevný, prespecified počet vláken se správně spustit.  Vzhledem k tomu, že výchozí nastavení pro dynamické úpravy počtu vláken, je definováno implementací, těchto programů můžete vypnout funkci dynamického vláken a nastavit počet vláken explicitně zajistit přenositelnost. Následující příklad ukazuje, jak to udělat pomocí [omp_set_dynamic –](3-run-time-library-functions.md#317-omp_set_dynamic-function), a [omp_set_num_threads –](3-run-time-library-functions.md#311-omp_set_num_threads-function):

```cpp
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

V tomto příkladu se program spustí správně pouze v případě, že se provede 16 vlákny. Pokud implementace nebude schopný zajistit podporu 16 vlákna, chování v tomto příkladu je definováno implementací.

Počet vláken v paralelní oblasti zůstává konstantní během paralelní oblasti, bez ohledu na nastavení dynamické vlákna. Mechanismus dynamické vlákna určuje počet vláken na začátku paralelní oblasti a zachová konstantní po dobu trvání oblast.

## <a name="a12-the-atomic-directive"></a>A.12 direktivy atomic

V následujícím příkladu se vyhnete konfliktům časování (souběžné aktualizace prvku *x* mnoha vlákny) s použitím [atomické](2-directives.md#264-atomic-construct) – direktiva:

```cpp
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

Výhodou použití `atomic` – direktiva v tomto příkladu je, že umožňuje aktualizace dvě různé prvky x být provedeny souběžně. Pokud [kritické](2-directives.md#262-critical-construct) – direktiva je místo toho použít, a pak aktualizuje všechny prvky *x* jsou prováděny sériově (i když není v žádném zaručené pořadí).

`atomic` – Direktiva se vztahuje pouze na okamžitě následující příkaz jazyka C nebo C++.  V důsledku toho prvky *y* se neaktualizují atomicky v tomto příkladu.

## <a name="a13-a-flush-directive-with-a-list"></a>A.13 A direktivy flush se seznamem

V následujícím příkladu `flush` direktivu pro typu point-to-point synchronizace konkrétních objektů mezi dvojice vláken:

```cpp
int   sync[NUMBER_OF_THREADS];
float work[NUMBER_OF_THREADS];
#pragma omp parallel private(iam,neighbor) shared(work,sync)
{
    iam = omp_get_thread_num();
    sync[iam] = 0;
    #pragma omp barrier

    // Do computation into my portion of work array
    work[iam] = ...;

    //  Announce that I am done with my work
    // The first flush ensures that my work is
    // made visible before sync.
    // The second flush ensures that sync is made visible.
    #pragma omp flush(work)
    sync[iam] = 1;
    #pragma omp flush(sync)

    // Wait for neighbor
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;
    while (sync[neighbor]==0)
    {
        #pragma omp flush(sync)
    }

    // Read neighbor's values of work array
    ... = work[neighbor];
}
```

## <a name="a14-a-flush-directive-without-a-list"></a>A.14 A direktivy flush bez seznamu

V následujícím příkladu (pro [části 2.6.5](2-directives.md#265-flush-directive)) odlišuje sdílené objekty vliv `flush` s žádný seznam sdílených objektů, které nejsou ovlivněny:

```cpp
// omp_flush_without_list.c
#include <omp.h>

int x, *p = &x;

void f1(int *q)
{
    *q = 1;
    #pragma omp flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

void f2(int *q)
{
    #pragma omp barrier
    *q = 2;

    #pragma omp barrier
    // a barrier implies a flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

int g(int n)
{
    int i = 1, j, sum = 0;
    *p = 1;

    #pragma omp parallel reduction(+: sum) num_threads(10)
    {
        f1(&j);
        // i, n and sum were not flushed
        //   because they were not accessible in f1
        // j was flushed because it was accessible
        sum += j;
        f2(&j);
        // i, n, and sum were not flushed
        //   because they were not accessible in f2
        // j was flushed because it was accessible
        sum += i + j + *p + n;
    }
    return sum;
}

int main()
{
}
```

## <a name="a15-the-number-of-threads-used"></a>A.15 počtu použitých vláken

Podívejte se na následující příklad nesprávné (pro [části 3.1.2](3-run-time-library-functions.md#312-omp_get_num_threads-function)):

```cpp
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()` Volání vrátí hodnotu 1 v sériového portu části kódu, takže *np* bude vždy rovné 1 v předchozím příkladu. Pokud chcete zjistit počet vláken, která se nasadí pro paralelní oblasti, třeba volání uvnitř paralelní oblasti.

Následující příklad ukazuje, jak přepsat tento program bez zahrnutí dotaz na počet vláken:

```cpp
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```

## <a name="a16-locks"></a>A.16 zámků

V následujícím příkladu (pro [části 3.2](3-run-time-library-functions.md#32-lock-functions)), argumentu funkce zamykání by měla mít typ `omp_lock_t`, a že je potřeba vyprázdněte ji.  Funkce zamykání způsobit vláken na nečinnost při čekání na vstup do první kritický oddíl, ale provádět další činnosti při čekání na vstup do druhé.  `omp_set_lock` Funkce bloky, ale `omp_test_lock` funkce nemá povolení práce v `skip()` udělat.

```cpp
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```

## <a name="a17-nestable-locks"></a>A.17, Vnořitelných zámků

V následujícím příkladu (pro [části 3.2](3-run-time-library-functions.md#32-lock-functions)) ukazuje, jak lze pomocí vnořitelných zámek synchronizace aktualizací pro celé struktury i pro jeden z jejích členů.

```cpp
#include <omp.h>
typedef struct {int a,b; omp_nest_lock_t lck;} pair;

void incr_a(pair *p, int a)
{
    // Called only from incr_pair, no need to lock.
    p->a += a;
}

void incr_b(pair *p, int b)
{
    // Called both from incr_pair and elsewhere,
    // so need a nestable lock.

    omp_set_nest_lock(&p->lck);
    p->b += b;
    omp_unset_nest_lock(&p->lck);
}

void incr_pair(pair *p, int a, int b)
{
    omp_set_nest_lock(&p->lck);
    incr_a(p, a);
    incr_b(p, b);
    omp_unset_nest_lock(&p->lck);
}

void f(pair *p)
{
    extern int work1(), work2(), work3();
    #pragma omp parallel sections
    {
        #pragma omp section
            incr_pair(p, work1(), work2());
        #pragma omp section
            incr_b(p, work3());
    }
}
```

## <a name="a18-nested-for-directives"></a>A.18 vnořené direktivy for

Následující příklad `for` [vnořování direktiv](2-directives.md#29-directive-nesting) vyhovuje protože vnitřní a vnější `for` direktivy svázat s jinou paralelních oblastí:

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

Následující změna v předchozím příkladu je také kompatibilní:

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```

## <a name="a19-examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 příklady nesprávného vnoření work-sharing direktivy

Příklady v této části ilustrují [vnořování direktiv](2-directives.md#29-directive-nesting) pravidla.

V následujícím příkladu je nekompatibilní protože vnitřní a vnější `for` direktivy jsou vnořené a vytvořit vazbu na stejný `parallel` – direktiva:

```cpp
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

Následující verze dynamicky vnořené v předchozím příkladu je také nedodržující předpisy:

```cpp
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

V následujícím příkladu je nekompatibilní vzhledem k tomu, `for` a `single` direktivy jsou vnořené a jejich připojení ke stejné paralelní oblasti:

```cpp
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

V následujícím příkladu je nekompatibilní protože `barrier` direktivy uvnitř `for` může vést k zablokování:

```cpp
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

V následujícím příkladu je nekompatibilní vzhledem k tomu, `barrier` výsledkem zablokování skutečnost, že pouze jedno vlákno najednou můžete zadat důležité části:

```cpp
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

V následujícím příkladu je nekompatibilní vzhledem k tomu, `barrier` výsledkem zablokování skutečnost, že provede pouze jedno vlákno `single` části:

```cpp
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```

## <a name="a20-bind-barrier-directives"></a>Direktiv barrier A.20 vazby

Vazby direktiv pravidla pro volání `barrier` směrnice vytvořit vazbu na nejbližší uzavírající `parallel` směrnice. Další informace o vazby direktiv, naleznete v tématu [části 2.8](2-directives.md#28-directive-binding).

V následujícím příkladu volání z *hlavní* k *sub2* je kompatibilní s protože `barrier` (v *sub3*) vytvoří vazbu paralelní oblastí v *sub2* . Volání z *hlavní* k *sub1* je kompatibilní s protože `barrier` váže k paralelní oblastí v podprogram *sub2*.  Volání z *hlavní* k *sub3* vyhovuje protože `barrier` bez vazby v jakémkoli paralelní oblasti a je ignorován. Také `barrier` synchronizuje pouze týmu vlákna v nadřazeném paralelní oblasti a ne všechna vlákna vytvořená v *sub1*.

```cpp
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```

## <a name="a21-scope-variables-with-the-private-clause"></a>A.21 rozsah platnosti proměnných rozsahu s klauzulí private

Hodnoty `i` a `j` v následujícím příkladu jsou definovaná na ukončení paralelní oblasti:

```cpp
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

Další informace o `private` klauzule, naleznete v tématu [části 2.7.2.1](2-directives.md#2721-private).

## <a name="a22-the-defaultnone-clause"></a>A.22 klauzule default(none)

Následující příklad odlišuje proměnné, které se vztahuje `default(none)` klauzule z proměnné, které nejsou:

```cpp
// openmp_using_clausedefault.c
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int x, y, z[1000];
#pragma omp threadprivate(x)

void fun(int a) {
   const int c = 1;
   int i = 0;

   #pragma omp parallel default(none) private(a) shared(z)
   {
      int j = omp_get_num_thread();
             //O.K.  - j is declared within parallel region
      a = z[j];       // O.K.  - a is listed in private clause
                      //      - z is listed in shared clause
      x = c;          // O.K.  - x is threadprivate
                      //      - c has const-qualified type
      z[i] = y;       // C3052 error - cannot reference i or y here

      #pragma omp for firstprivate(y)
         for (i=0; i<10 ; i++) {
            z[i] = y;  // O.K. - i is the loop control variable
                       // - y is listed in firstprivate clause
          }
       z[i] = y;   // Error - cannot reference i or y here
   }
}
```

Další informace o `default` klauzule, naleznete v tématu [části 2.7.2.5](2-directives.md#2725-default).

## <a name="a23-examples-of-the-ordered-directive"></a>A.23 příklady seřazený – direktiva

Je možné mít mnoho seřazený oddíly se `for` zadaný `ordered` klauzule. První příklad nedodržuje předpisy, protože rozhraní API určuje následující pravidlo:

"Iterace smyčky s `for` konstrukce nesmí spustit stejný `ordered` direktiv více než jednou a nesmí spuštění více než jedné `ordered` – direktiva." (Viz [části 2.6.6](2-directives.md#266-ordered-construct).)

V tomto příkladu nedodržující předpisy spuštění všech iterací dvou seřazených oddílů:

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

Následující příklad, který je kompatibilní `for` s více než jednu uspořádanou sekci:

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```

## <a name="a24-example-of-the-private-clause"></a>A.24 příklady použití klauzule private

[Privátní](2-directives.md#2721-private) klauzule paralelní oblasti je platná pouze pro lexikální rozsah oblast, nikoli pro dynamický rozsah oblasti.  Proto v příkladu, který následuje, všechny používá proměnnou *a* v rámci `for` smyčky v rutině *f* odkazuje privátní kopie *a*, při použití v rutiny *g* odkazuje na globální *a*.

```cpp
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```

## <a name="a25-examples-of-the-copyprivate-data-attribute-clause"></a>A.25 příklady klauzule copyprivate data atributu

**Příklad 1:** [Copyprivate](2-directives.md#2728-copyprivate) klauzuli lze použít k vysílání hodnoty získané jedno vlákno přímo na všechny instance soukromé proměnné v jiných vláken.

```cpp
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

Pokud rutiny *init* nazývá ze sériového portu oblasti své chování nemá vliv na přítomnost direktivy. Po zavolání *get_values* rutiny provedl jedním vláknem, žádný přístup z více vláken opustí konstruktu dokud privátní objekty určené, které *a*, *b*, *x*, a *y* v všechna vlákna stát definovali s hodnotami pro čtení.

**Příklad 2:** Na rozdíl od předchozího příkladu předpokládejme, že čtení se musí provádět konkrétní vlákno, Dejme tomu, že hlavní vlákno. V takovém případě `copyprivate` klauzuli nelze použít přímo provedete vysílání, ale je možné poskytnout přístup ke sdílené dočasný objekt.

```cpp
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**Příklad 3:** Předpokládejme, že počet objektů zámek vyžaduje v rámci paralelní oblasti, které nelze snadno určit ještě než ho přidáte. `copyprivate` Klauzuli lze použít pro poskytnutí přístupu k sdílený zámek objekty, které jsou přiděleny v rámci dané paralelní oblasti.

```cpp
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```

## <a name="a26-the-threadprivate-directive"></a>A.26 threadprivate – direktiva

Následující příklady ukazují, jak používat [threadprivate](2-directives.md#271-threadprivate-directive) směrnice poskytnout samostatné čítač každé vlákno.

### <a name="example-1"></a>Příklad 1

```cpp
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

### <a name="example-2"></a>Příklad 2

```cpp
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```

## <a name="a27-c99-variable-length-arrays"></a>A.27 polí proměnné délky C99

Následující příklad ukazuje způsob použití polí proměnné délky (VLAs) C99 v [firstprivate](2-directives.md#2722-firstprivate) směrnice.

> [!NOTE]
> Pole s proměnnou délkou se momentálně nepodporují v jazyce Visual C++.

```cpp
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```

## <a name="a28-the-numthreads-clause"></a>A.28 klauzule num_threads

Následující příklad ukazuje, [num_threads](2-directives.md#23-parallel-construct) klauzuli. S maximálně 10 vláken provádí paralelní oblasti.

```cpp
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```

## <a name="a29-work-sharing-constructs-inside-a-critical-construct"></a>A.29 konstrukce pro sdílení práce uvnitř konstrukce critical

Následující příklad ukazuje použití sdílení práce uvnitř konstrukce `critical` vytvořit. V tomto příkladu je kompatibilní, protože sdílení práce vytvořit a `critical` konstruktor není vázán na stejné paralelní oblasti.

```cpp
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```

## <a name="a30-reprivatization"></a>A.30 Reprivatization

Následující příklad ukazuje reprivatization proměnné. Soukromé proměnné je možné označit `private` znovu za vnořená direktiva. Nemusíte sdílejí tyto proměnné v ohraničujícím paralelní oblasti.

```cpp
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```

## <a name="a31-thread-safe-lock-functions"></a>A.31 funkce zamykání bezpečné pro vlákna

Následující C++ příklad ukazuje, jak inicializovat pole zámky v paralelní oblasti s použitím [omp_init_lock](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions).

```cpp
// A_13_omp_init_lock.cpp
// compile with: /openmp
#include <omp.h>

omp_lock_t *new_locks() {
   int i;
   omp_lock_t *lock = new omp_lock_t[1000];
   #pragma omp parallel for private(i)
   for (i = 0 ; i < 1000 ; i++)
      omp_init_lock(&lock[i]);

   return lock;
}

int main () {}
```
