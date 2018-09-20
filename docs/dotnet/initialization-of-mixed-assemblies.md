---
title: Inicializace smíšených sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ba9f3143fb110b25f384e462e7dfcd69c0140802
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439572"
---
# <a name="initialization-of-mixed-assemblies"></a>Inicializace smíšených sestavení

Vývojáři Windows musí být opatrně zámek zavaděče při spuštění kódu během `DllMain`. Existují však některé další důležité informace, které souvisejí při práci s C + +/ clr sestavení ve smíšeném režimu.

Kód v rámci [DllMain](/windows/desktop/Dlls/dllmain) nesmí přístup k modulu CLR. To znamená, že `DllMain` by měla volat žádné spravované funkce, přímo nebo nepřímo; žádný spravovaný kód by měl být deklarován nebo implementované v `DllMain`; a žádná uvolnění paměti nebo automatické načítání knihovna má být provedena v rámci `DllMain` .

## <a name="causes-of-loader-lock"></a>Příčiny zámek zavaděče

Po zavedení služby na platformě .NET jsou dva odlišné mechanismy pro načítání modul spuštění (EXE nebo DLL): jeden pro Windows, který se používá pro nespravované moduly, a jeden pro .NET CLR Common Language Runtime (), která načte sestavení .NET. Smíšené problém načtení knihovny DLL se soustředí kolem zavaděč operačního systému Microsoft Windows.

Pokud je načten do procesu sestavení obsahující pouze .NET konstrukce, zavaděč modulu CLR, provést všechny potřebné úkoly inicializace a načítání samotný. Ale pro smíšená sestavení, protože mohou obsahovat nativní kód a data, zavaděč Windows musí také možné používat.

Zavaděč Windows zaručuje, že žádný kód můžete přístupový kód nebo data v této knihovně DLL předtím, než byl inicializován a že žádný kód můžete redundantně načíst knihovnu DLL při částečně je inicializován. K tomuto účelu zavaděč Windows používá globální procesu kritický oddíl (často označované jako "zámek zavaděče"), který zabrání unsafe přístupu při inicializaci modulu. V důsledku toho je citlivé na řadu scénářů classic zablokování procesu načítání. Následující dva scénáře pro smíšená sestavení, zvyšte riziku zablokování:

- První, pokud se uživatelé pokusí spustit funkce zkompilované do jazyk Microsoft intermediate language (MSIL), pokud je držen zámek zavaděče (z `DllMain` nebo statické inicializátory, například), může dojít k zablokování. Vezměte si situaci, ve kterém funkce jazyka MSIL odkazuje na typ v sestavení, který není načtený. Modul CLR se pokusí automaticky načíst toto sestavení, které mohou vyžadovat Windows zavaděče blokovat zámek zavaděče. Protože kódu výše v pořadí volání je již drží zámek zavaděče, zablokování výsledků. Ale provádění MSIL nastavený zámek zavaděče není zaručeno, že dojde k zablokování, ztěžuje tento scénář tak diagnostikovat a opravit. V některých případech jako je například, pokud knihovna DLL odkazovaného typu obsahuje žádné nativní konstrukce a všechny jeho závislosti neobsahují žádné nativní konstrukce Windows zavaděče není nutné k načtení sestavení .NET odkazovaného typu. Kromě toho požadované sestavení nebo jeho závislosti smíšená nativní/.NET může již byly načteny jiným kódem. V důsledku toho vzájemné zablokování může být obtížné odhadnout a může lišit v závislosti na konfiguraci cílového počítače.

- Za druhé při načítání knihovny DLL ve verzích 1.0 a 1.1 rozhraní .NET Framework, modul CLR předpokládá, že nebyl držen zámek zavaděče a provést několik akcí, které jsou neplatné nastavený zámek zavaděče. Za předpokladu, že není držen zámek zavaděče je platný předpokladů pro čistě knihovny DLL .NET, ale protože smíšených knihoven DLL spustit nativní inicializační rutiny, vyžadují nativní zavaděč Windows a proto zámek zavaděče. V důsledku toho i v případě, že vývojář nebyl pokusu o provedení žádné funkce jazyka MSIL během inicializace knihovny DLL, se stále malá možnost nedeterministická zablokování pomocí verze 1.0 a 1.1 rozhraní .NET Framework.

Všechny seznam byl odebrán z procesu načítání smíšených knihoven DLL. To bylo provedeno pomocí tyto změny:

- Při načítání smíšených knihoven DLL, CLR už díky false předpoklady.

- Nespravovaná a spravovaná inicializace probíhá ve dvou fázích samostatné a odlišné. Nespravované inicializace probíhá nejprve (prostřednictvím funkce DllMain) a spravovaný inicializace probíhá později, až. Konstrukce podporované NET volána *.cctor*. Druhá možnost je pro uživatele zcela transparentní. není-li **/Zl** nebo **: / NODEFAULTLIB** se používají. Zobrazit[: / NODEFAULTLIB (ignorování knihoven)](../build/reference/nodefaultlib-ignore-libraries.md) a [/Zl (vynechat název výchozí knihovny)](../build/reference/zl-omit-default-library-name.md) Další informace.

Zámek zavaděče může stále dojít, ale nyní reprodukovatelná dochází a je zjištěn. Pokud `DllMain` obsahuje instrukce jazyka MSIL, kompilátor vygeneruje upozornění [upozornění kompilátoru (úroveň 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Kromě toho CRT nebo modulu CLR se pokusí rozpoznat a ohlásit pokusí spustit jazyk MSIL nastavený zámek zavaděče. Detekce CRT výsledků v modulu runtime R6033 diagnostických C Run-Time chyba jazyka.

Zbývající část tohoto dokumentu popisuje scénáře zbývající, pro které můžete spustit jazyk MSIL zámek zavaděče řešení problému v každém z těchto scénářů a techniky ladění.

## <a name="scenarios-and-workarounds"></a>Scénáře a řešení

Existuje několik různých situacích, kdy může uživatel provést kód jazyka MSIL nastavený zámek zavaděče. Vývojář musí zajistit, že implementace kódu uživatele nebude pokoušet pro spouštění instrukcí jazyka MSIL pod každým z těchto okolností. Následující témata popisují všechny možnosti s diskusi o tom, jak vyřešit problémy v nejběžnějších případech.

### <a name="dllmain"></a>Zpracování funkce DllMain

`DllMain` Funkce je vstupním bodem definované uživatelem pro knihovnu DLL. Pokud uživatel neurčí jinak, `DllMain` je vyvolána pokaždé, když proces nebo vlákno připojí nebo odpojí od obsahující knihovnu DLL. Protože toto volání může dojít, dokud je držen zámek zavaděče, ne uživatelem zadané `DllMain` funkce by měla být zkompilována do jazyka MSIL. Kromě toho se žádná funkce ve stromu volání kořenovým adresářem v `DllMain` mohou být zkompilována do jazyka MSIL. Chcete-li vyřešit problémy většinou neřeší, blok kódu, který definuje `DllMain` by měl být upraven pomocí #pragma `unmanaged`. Stejné by měla provést pro každou funkci, která `DllMain` volání.

V případech, kde tyto funkce musí volat funkci, která vyžaduje implementaci jazyka MSIL pro jiné kontexty volání duplikace strategie je možné kde jsou vytvářeny .NET a nativní verzi stejnou funkci.

Případně pokud `DllMain` nevyžaduje nebo pokud není nutné provádět v rámci zavaděč uzamčení, pokud uživatel `DllMain` implementace může být odebrána, které dojde k odstranění problému.

Pokud se pokusí spustit jazyk MSIL přímo, zpracování funkce DllMain [upozornění kompilátoru (úroveň 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) dojde. Kompilátor však nemůže rozpoznat případy, kdy zpracování funkce DllMain volá funkci v další modul, který se pak pokusí spustit jazyk MSIL.

Další informace o tomto scénáři najdete v článku "Překážky pro diagnostiku".

### <a name="initializing-static-objects"></a>Inicializace statických objektů

Inicializace statických objektů může způsobit zablokování, pokud je potřeba dynamických inicializátorů. Jednoduché v případech, například když je statická proměnná jednoduše přiřadit hodnotu v době kompilace znám žádný dynamická inicializace je požadovaná, proto neexistuje žádný riziku zablokování. Však statické proměnné inicializován pomocí volání funkce, vyvolání konstruktoru nebo výrazy, které nelze vyhodnotit za kompilace všechny vyžadují kód ke spuštění během inicializace modulu.

Následující kód ukazuje příklady statické inicializátory, které vyžadují dynamická inicializace: volání funkce, vytváření objektu a inicializace ukazatele. (Tyto příklady nejsou statické, ale předpokládá, že jsou definovány v globálním rozsahu, který má stejný účinek.)

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

Toto riziko zablokování závisí na tom, zda je kompilován obsahující modul **/CLR** a určuje, zda bude proveden jazyka MSIL. Konkrétně Pokud statická proměnná je kompilován bez **/CLR** (nebo se nachází v #pragma `unmanaged` bloku), a dynamického inicializátoru potřebné k inicializaci je výsledkem spuštění instrukce jazyka MSIL, může dojít k zablokování. Důvodem je, že pro moduly zkompilované bez **/CLR**, inicializace statických proměnných se provádí pomocí funkce DllMain. Naproti tomu statické proměnné zkompilovaná **/CLR** jsou inicializovány .cctor po dokončení fáze inicializace nespravované a byla vydána zavaděči.

Existuje mnoho řešení k vzájemnému zablokování způsobené dynamická inicializace statických proměnných (přibližně uspořádány v pořadí podle čas potřebný k vyřešení problému):

- Zdrojový soubor obsahující statickou proměnnou, může být zkompilován s **/CLR**.

- Všechny funkce volána statická proměnná nemůže být zkompilována pro nativní kód pomocí #pragma `unmanaged` směrnice.

- Ručně zkopírujte kód, který statická proměnná závisí, poskytování .NET a nativní verzi s různými názvy. Vývojářům můžete volat nativní verzi z nativní statické inicializátory a volání rozhraní .NET verze jinde.

### <a name="user-supplied-functions-affecting-startup"></a>Uživatelem zadané funkce by to ovlivnilo po spuštění

Existuje několik uživatelem zadané funkce, na kterých závisí knihovny pro inicializaci během spouštění. Například když globálně přetížení operátorů v jazyce C++, jako `new` a `delete` operátory, verze zadané uživatele jsou použít kdekoli, včetně inicializace standardní knihovny C++ a zničení. V důsledku toho standardní knihovny C++ a uživatelem zadané statické inicializátory vyvolá uživatelem zadaný verze těchto operátorů.

Pokud verze zadané uživatele jsou zkompilovány do jazyka MSIL, pak tyto inicializátory zkusíte pro spouštění instrukcí jazyka MSIL, dokud je držen zámek zavaděče. Uživatelem zadané `malloc` má stejné důsledky. Chcete-li vyřešit tento problém, některý z těchto přetížení nebo uživatelem zadané definice musí implementovány v nativním kódu s využitím #pragma `unmanaged` směrnice.

Další informace o tomto scénáři najdete v článku "Překážky pro diagnostiku".

### <a name="custom-locales"></a>Vlastní národní prostředí

Pokud uživatel zadá vlastní globální národní prostředí, toto národní prostředí se použije pro všechny budoucí vstupně-výstupních operací datové proudy, včetně těch, které jsou staticky inicializovat inicializace. Pokud je tento objekt globální národní prostředí zkompilována do jazyka MSIL, může objekt národního prostředí členské funkce zkompilované na MSIL vyvolat, dokud je držen zámek zavaděče.

Existují tři možnosti pro řešení tohoto problému:

Zdrojové soubory obsahující všechny globální definice datového proudu vstupně-výstupní operace může být kompilováno s použitím **/CLR** možnost. To zabrání jejich statické inicializátory být prováděn nastavený zámek zavaděče.

Definice funkcí vlastní národní prostředí můžete zkompilované do nativního kódu s použitím #pragma `unmanaged` směrnice.

Zdrží nastavení vlastní národní prostředí jako globální národní prostředí až po vydání zámek zavaděče. Potom nakonfigurujte explicitně vstupně-výstupních operací datové proudy vytvořené během inicializace s vlastní národní prostředí.

## <a name="impediments-to-diagnosis"></a>Překážky pro diagnostiku

V některých případech je obtížné rozpoznat příčiny zablokování. Následující témata popisují tyto scénáře a způsoby, jak tyto problémy obejít.

### <a name="implementation-in-headers"></a>Implementace v záhlaví

V případech, select může zkomplikovat implementace funkce uvnitř hlavičkové soubory diagnostiky. Vložené funkce a kód šablony vyžadují, aby byl specifikován funkce v hlavičkovém souboru.  Jazyk C++ určuje jednoho definičního pravidla, která vynutí všechny implementace funkcí se stejným názvem jako sémanticky ekvivalentní. V důsledku toho linkeru C++ nemusí provést žádná zvláštní opatření, při slučování souborů objektů, které mají duplicitní implementace dané funkce.

Před Visual Studio 2005 linker jednoduše zvolí největší tyto sémantické ekvivalenty definic, tak, aby vyhovovaly deklarace dopředu a scénáře, pokud možnosti různých optimalizace se používá pro jiné zdrojové soubory. Vzniká tak problém pro smíšená nativní/.NET knihovny DLL.

Vzhledem k tomu může být stejná hlavička zahrnuté i souborů C++ s **/CLR** povolené a zakázané, nebo #include dá zabalit uvnitř #pragma `unmanaged` blok, je možné mít jazyk MSIL i nativní verze funkcí, které poskytují implementace v záhlaví. Jazyk MSIL a nativní implementace mají různou sémantiku s ohledem na inicializaci zámek zavaděče, což účinně porušuje pravidlo jednu definici. V důsledku toho když linker vybere největší implementace, je rozhodnout MSIL verzi funkce, i v případě, že explicitně byl kompilován do nativního kódu jinde pomocí směrnice #pragma unmanaged. Aby bylo zajištěno, že je nastavený zámek zavaděče nikdy volána MSIL verzi šablony nebo vloženou funkci, musí každá definice každé funkce volána nastavený zámek zavaděče upravit pomocí #pragma `unmanaged` směrnice. Pokud hlavičkový soubor od třetích stran, vkládat a vyvolat přes pop nespravované Direktiva #pragma kolem je nejjednodušší způsob, jak toho dosáhnout #include – direktiva problematický souboru hlaviček. (Viz [spravované, nespravované](../preprocessor/managed-unmanaged.md) příklad.) Tato strategie však nebude fungovat pro hlavičky, které obsahují jiný kód, který se musí volat přímo rozhraní API pro .NET.

V zájmu usnadnění práce pro uživatele pracující s zámek zavaděče linker zvolí nativní implementaci přes spravované převedou s oběma. Tím se vyhnete výše uvedené problémy. Nicméně existují dvě výjimky z tohoto pravidla v této verzi z důvodu dvou nevyřešené problémy s kompilátor:

- Volání je vložená funkce se prostřednictvím ukazatele globální statické funkce. Tento scénář je obzvláště důležité, protože jsou virtuální funkce volány prostřednictvím ukazatele na globální funkce. Například

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>Diagnostika v režimu ladění

Všechny Diagnostika zámek zavaděče, které by mělo být provedeno problémy s ladicí sestavení. Sestavení pro vydání nemusí poskytovat diagnostiky a optimalizace provedené v režimu vydání může maskovat některý jazyk MSIL podle scénáře zámek zavaděče.

## <a name="how-to-debug-loader-lock-issues"></a>Jak ladit problémy zámek zavaděče

Diagnostiky, které generuje modul CLR při vyvolání funkce jazyka MSIL způsobí, že modul CLR k pozastavení provádění. Naopak to způsobí, že ladicí program Visual C++ ve smíšeném režimu se také pozastavení při spuštění laděného procesu v rámci procesu. Ale při připojování k procesu, není možné získat spravované zásobník volání pro laděný proces pomocí smíšené ladicího programu.

Vývojáři by k identifikaci konkrétní funkce jazyka MSIL, která byla volána nastavený zámek zavaděče, proveďte následující kroky:

1. Ujistěte se, že jsou k dispozici symboly pro knihovny mscoree.dll a knihovny mscorwks.dll.

   To lze provést dvěma způsoby. Soubory PDB pro knihovny mscoree.dll a knihovny mscorwks.dll nejprve, lze přidat do cesty pro hledání symbolů. Chcete-li to provést, otevřete dialogové okno Možnosti cesty hledání symbolů. (Z **nástroje** nabídce zvolte **možnosti**. V levém podokně **možnosti** dialogovém okně Otevřít **ladění** uzlu a zvolte **symboly**.) Přidáte cestu do knihovny mscoree.dll a knihovny mscorwks.dll soubory PDB do seznamu hledání. Na % VSINSTALLDIR%\SDK\v2.0\symbols se nainstalují tyto soubory PDB. Zvolte **OK**.

   Za druhé soubory PDB pro knihovny mscoree.dll a knihovny mscorwks.dll můžete stáhnout ze serveru symbolů Microsoft. Pokud chcete nakonfigurovat Server symbolů, otevřete dialogové okno Možnosti cesty hledání symbolů. (Z **nástroje** nabídce zvolte **možnosti**. V levém podokně **možnosti** dialogovém okně Otevřít **ladění** uzlu a zvolte **symboly**.) Přidejte následující cesty pro hledání do seznamu hledání: http://msdl.microsoft.com/download/symbols. Přidejte adresář mezipaměti symbolů do textového pole symbol server mezipaměti. Zvolte **OK**.

1. Nastavte režim ladění na nativní režim.

   Chcete-li to provést, otevřete **vlastnosti** mřížky pro spouštěný projekt v řešení. Vyberte **vlastnosti konfigurace** > **ladění**. Nastavte **typ ladicího programu** k **jenom nativní**.

1. Spuštění ladicího programu (F5).

1. Když **/CLR** diagnostiky se vygeneruje, zvolte **opakujte** a klikněte na tlačítko **přerušit**.

1. Otevřete okno zásobníku volání. (Na řádku nabídek zvolte **ladění** > **Windows** > **zásobník volání**.) Je problematický `DllMain` nebo statický inicializátor se určuje podle zelenou šipku. Pokud problematický funkce není určena, následující kroky třeba ji najít.

1. Otevřít **okamžité** okna (v řádku nabídek zvolte **ladění** > **Windows** > **okamžité**.)

1. Typ knihovny sos.dll .load do **okamžité** okna pro načtení ladění služby SOS.

1. Typ! dumpstack do **okamžité** okno získat úplný seznam všech vnitřní **/CLR** zásobníku.

1. Vyhledejte první instance (co nejblíž koncovým dolního okraje zásobníku) buď _cordllmain – (Pokud `DllMain` způsobí, že problém) nebo _VTableBootstrapThunkInitHelperStub nebo GetTargetForVTableEntry (Pokud je statický inicializátor způsobí, že problém). Položka zásobníku přímo pod toto volání není že implementovaná funkce, která se pokusila provést nastavený zámek zavaděče volání MSIL.

1. Přejít do zdrojového souboru a číslo identifikován v předchozím kroku a správné řádku potíže s použitím scénáře a řešení popsaných v části scénáře.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje, jak se vyhnout zámek zavaděče přesunutím kód z `DllMain` do konstruktoru objektu globálního objektu.

V této ukázce je globální spravovaný objekt, jehož konstruktor obsahuje spravovaný objekt, který byl původně v `DllMain`. Druhá část této ukázce odkazuje na sestavení, vytvoření instance spravovaný objekt, která se má vyvolat konstruktor modul, který provede inicializaci.

### <a name="code"></a>Kód

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker does not throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

Tento příklad ukazuje problémy v inicializace smíšených sestavení:

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

Tento kód vytvoří následující výstup:

```Output
Module ctor initializing based on global instance of class.

Test called so linker does not throw away unused object.
```

## <a name="see-also"></a>Viz také:

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
