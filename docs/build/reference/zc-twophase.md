---
title: "/Zc:twoPhase-(zakázat dvoufázového název vyhledávání) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4582a5532d9fd410224ee4174ca3973bfe539656
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-(zakázat dvoufázového název vyhledávání)

Když **/Zc:twoPhase-** je zadána možnost, kompilátor analyzuje a vytvoří instance šablony třídy a funkce nonkonformní stejně jako verze sady Visual Studio před Visual Studio 2017 verze 15.3. 

## <a name="syntax"></a>Syntaxe

> **/Zc:twoPhase-**

## <a name="remarks"></a>Poznámky

Ve Visual Studio 2017 verze 15.3 a novější, ve výchozím nastavení používá kompilátor vyhledávání dvoufázového názvu pro rozlišení názvu šablony. Pokud **/Zc:twoPhase-** není zadaný, kompilátor přejde do své předchozí nonkonformní třída šablony a funkce šablony název překlad IP adres a nahrazení chování.

**/Zc:twoPhase-** ve výchozím nastavení není nastavena možnost povolit nonkonformní chování. [/ Projektovou-](permissive-standards-conformance.md) možnost implicitně nastaví vyhovující chování kompilátoru dvoufázového vyhledávání, ale můžete přepsat pomocí **/Zc:twoPhase-**.

Soubory hlaviček Windows SDK ve verzi 10.0.15063.0 (Creators aktualizace nebo Redstone 2) a starší verze v režimu shoda nefungují správně. Je nutné použít **/Zc:twoPhase-** zkompilovat kód pro tyto verze sady SDK, pokud používáte verzi Visual Studio 2017 15.3 a novější verze. Verze sady Windows SDK pro počínaje verzí 10.0.15254.0 (Redstone 3 nebo patří Creators aktualizace) v režimu shoda fungovat správně a nevyžadují **/Zc:twoPhase-** možnost.

Použití **/Zc:twoPhase-** Pokud kódu vyžaduje staré chování pro správnou kompilaci. Důrazně zvažte aktualizaci kódu tak, aby odpovídala standardní.

### <a name="compiler-behavior-under-zctwophase-"></a>Chování kompilátoru pod /Zc:twoPhase-

Ve verzích kompilátoru před Visual Studio 2017 verze 15.3 a kdy **/Zc:twoPhase-** není zadaný, kompilátor použije toto chování:

- Analyzuje jej pouze deklaraci šablony, head třídy a seznamu základní třídy. Šablona textu se zaznamená jako tokenu datového proudu. Žádné funkce subjekty, inicializátory, výchozí argumenty nebo noexcept argumenty jsou analyzovány. Šablona třídy je vytvořena instance pseudo ve typu předběžné ověření, zda deklarace v šabloně třídy jsou správné. Vezměte v úvahu tato šablona třídy:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   Deklaraci šablony `template <typename T`>, head – třída `class Derived`a seznam základní třídy `public Base<T>` jsou analyzovat, ale text šablony se zaznamená jako tokenu datového proudu.

- Při analýze šablonu funkce, kompilátor analyzuje pouze podpis funkce. Tělo funkce je nikdy analyzovat. Místo toho se zaznamená jako tokenu datového proudu.

Výsledkem je Pokud šablony text obsahuje chyby syntaxe a nikdy vytvoření instance šablony, chyby se nikdy diagnostice.

Jiné účinku toto chování je rozlišení přetížení. Kvůli způsobu, kterým token datový proud je rozšířena v lokalitě vytváření instancí znaky, které nebyly viditelné v deklaraci šablony mohou být viditelné v okamžiku vytvoření instance a účastnit rozlišení přetížení. To může vést k šablony, které mění chování v závislosti na kód, který nebyl viditelné, když šablona byla definována rozporu s touto standardní.

Podívejte se například na tento kód:

```cpp
#include <cstdio>

void func(void*) { std::puts("The call resolves to void*") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("The call resolves to int"); }

int main() 
{
    g(3.14);
}
```

Při kompilaci v části **/Zc:twoPhase-**, tento program vytiskne "volání řeší na celá čísla". V režimu shoda v rámci **/ projektovou-**, tento program vytiskne "volání přeloží na void *", protože druhý přetížení z `func` není viditelný, když kompilátor narazí šablony.

*Názvy závislých prvků*, názvy, které závisí na parametru šablony, mají chování vyhledávání, které se také liší pod **/Zc:twoPhase-**. V režimu shoda nejsou v místě definice šablony vázán názvy závislých prvků. Místo toho při vytváření instance šablony jsou vyhledávat tyto názvy. Pro volání funkce s názvem závislé funkce že název je svázaný sadu funkcí, které jsou viditelné v místě volání v definici šablony, jak je uvedeno výše. Další přetížení z závislého na argumentu vyhledávání jsou přidány na bod definice šablony a bod kde dojde k vytvoření instance šablony. Dvě fáze dvoufázového vyhledávání jsou vyhledávání pro názvy nezávislých v době definice šablony a vyhledávání pro názvy závislých prvků v době vytvoření instance šablony. V části **/Zc:twoPhase-**, kompilátor neprovádí vyhledávání závislého na argumentu samostatně z obyčejnou, neúplné vyhledávání (tedy nedělá dvoufázového vyhledávání), takže výsledky rozlišení přetížení se můžou lišit.

Zde je další příklad:

```cpp
// zctwophase1.cpp
// Compile by using
// cl /EHsc /W4 /permissive- zctwophase1.cpp
// cl /EHsc /W4 /permissive- /Zc:twoPhase- zctwophase1.cpp

#include <cstdio>

void func(long) { std::puts("func(long)"); }

template <typename T> void tfunc(T t) {
    func(t);
}

void func(int) { std::puts("func(int)"); }

namespace NS {
    struct S {};
    void func(S) { std::puts("NS::func(NS::S)"); }
}

int main() {
    tfunc(1729);
    NS::S s;
    tfunc(s);
}
```

Při kompilaci bez **/Zc:twoPhase-**, to vytiskne

```Output
func(long)
NS::func(NS::S)
```

Když kompilujete s **/Zc:twoPhase-**, to vytiskne

```Output
func(int)
NS::func(NS::S)
```

V režimu shoda v rámci **/ projektovou-**, volání `tfunc(1729)` přeloží na `void func(long)` přetížení není `void func(int)` přetížení jako v části **/Zc:twoPhase-**, protože neúplný `func(int)` je deklarovaný po definování šablony a prostřednictvím vyhledávání závislého na argumentu nebyl nalezen. Ale `void func(S)` účastnit závislého na argumentu vyhledávání, tak se přidá do přetížení nastavit pro volání `tfunc(s)` i když je deklarovaná po funkce šablony.

### <a name="update-your-code-for-two-phase-conformance"></a>Aktualizujte kód pro dvoufázového shoda

Starší verze kompilátoru nevyžadují klíčová slova `template` a `typename` všude, kde je C++ Standard vyžaduje. Tato klíčová slova jsou potřeba v některých pozice k rozlišení, jak analyzovat závislé název během první fáze vyhledávání kompilátory. Příklad:

`T::Foo<a || b>(c);`

Analyzuje vyhovující kompilátoru `Foo` jako proměnné v oboru `T`, což znamená, tento kód je logickou- nebo výraz s `T::foo < a` jako levý operand a `b > (c)` jako pravý operand. Pokud jste na mysli používat `Foo` jako šablona funkce, musí znamenat, že se šablona přidáním `template` – klíčové slovo:

`T::template Foo<a || b>(c);`

V verze starší než Visual Studio 2017 verze 15.3 a kdy **/Zc:twoPhase-** není zadaný, kompilátor umožňuje tento kód bez `template` – klíčové slovo a interpretuje ji jako volání šablony funkce s argumentem `a || b`, protože ji analyzuje šablony velmi omezená způsobem. Výše uvedený kód není vůbec analyzovat v první fázi. Během druhé fáze je dostatek kontextu říct, `T::Foo` je šablonu, nikoli proměnné, takže kompilátor nevynucuje použití klíčového slova.

Toto chování se zobrazí také odstraněním klíčové slovo `typename` před názvy subjektů šablony funkce, inicializátory, výchozí argumenty a noexcept argumenty. Příklad:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Pokud použijete klíčové slovo `typename` v těle funkce tento kód zkompiloval pod **/Zc:twoPhase-**, ale není v **/ projektovou-**. `typename` – Klíčové slovo je potřeba určit, že `TYPE` závisí. Protože není v části analyzovat tělo **/Zc:twoPhase-**, položka hierarchyinfoguid kompilátoru vyžadují klíčové slovo. V **/ projektovou-** režimu shoda, kód bez `typename` – klíčové slovo generuje chyby. K migraci kódu pro Visual Studio 2017 verze 15.3 a i mimo vložit `typename` – klíčové slovo tam, kde je chybí.

Podobně zvažte této ukázce kódu:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

V části **/Zc:twoPhase-** a starší kompilátory kompilátor pouze vyžaduje `template` – klíčové slovo na řádku 2. Ve výchozím nastavení a v režimu shoda, kompilátor teď taky vyžaduje `template` – klíčové slovo na řádku 4 k označení, že `T::X<T>` je šablonu. Vyhledejte kód, který chybí toto klíčové slovo a zadat, aby byl váš kód standardům.

Další informace o problémech s shoda najdete v tématu [vylepšení shoda C++ v sadě Visual Studio](../../cpp-conformance-improvements-2017.md) a [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc:twoPhase-** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
