---
title: Inicializace smíšených sestavení
ms.date: 03/09/2018
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 35dd47bd87c278d60fc616dca854bf843acc7c57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501231"
---
# <a name="initialization-of-mixed-assemblies"></a>Inicializace smíšených sestavení

Vývojáři systému Windows musí být při spuštění kódu v průběhu `DllMain`přistupují opatrně vždy uzamčen zavaděč. Existují však některé další problémy, které je potřeba vzít v úvahu při C++práci s/CLR sestaveními smíšeného režimu.

Kód v [DllMain](/windows/win32/Dlls/dllmain) nesmí přistupovat k modulu CLR (Common Language Runtime) .NET. To znamená `DllMain` , že by nemělo dělat žádná volání spravovaných funkcí přímo ani nepřímo; žádný spravovaný kód by neměl být deklarován nebo `DllMain`implementován v; a žádné uvolňování paměti nebo automatické načítání knihoven by `DllMain` nemělo probíhat v rámci .

## <a name="causes-of-loader-lock"></a>Příčiny zámku zavaděče

Při zavádění platformy .NET existují dva odlišné mechanismy pro načtení modulu spuštění (EXE nebo DLL): jeden pro systém Windows, který se používá pro nespravované moduly a jeden pro modul CLR, který načte sestavení .NET. Kombinovaná knihovna DLL načítající problém se pohybuje na střed zavaděče operačního systému Microsoft Windows.

Když je sestavení obsahující pouze konstrukce .NET načteno do procesu, zavaděč CLR může provést všechny nezbytné úlohy načítání a inicializace. Nicméně pro smíšená sestavení, protože mohou obsahovat nativní kód a data, musí být použit zavaděč systému Windows.

Zavaděč systému Windows zaručuje, že žádný kód nemůže získat přístup ke kódu nebo datům v této knihovně DLL předtím, než byl inicializován, a že žádný kód nemůže redundantní knihovnu DLL načítat při částečně inicializaci. K tomu zavaděč Windows používá oddíl kritický pro procesy (často se označuje jako "zámek zavaděče"), který zabraňuje nezabezpečenému přístupu během inicializace modulu. V důsledku toho je proces načítání zranitelný z řady klasických scénářů vzájemného zablokování. U smíšených sestavení zvyšuje riziko zablokování následující dva scénáře:

- Nejprve, pokud se uživatel pokusí spustit funkce zkompilované do jazyka MSIL (Microsoft Intermediate Language), když je držen zámek zavaděče `DllMain` (například z nebo ve statických inicializátorech), může způsobit zablokování. Vezměte v úvahu případ, ve kterém funkce jazyka MSIL odkazuje na typ v sestavení, které nebylo načteno. Modul CLR se pokusí toto sestavení automaticky načíst, což může vyžadovat, aby zavaděč systému Windows blokoval zámek zavaděče. Dojde k zablokování, protože zámek zavaděče již je držen kódem dříve v sekvenci volání. Spuštění jazyka MSIL v rámci zámku zavaděče však nezaručuje, že dojde k zablokování, což usnadňuje diagnostikování a opravu tohoto scénáře. V některých případech, například pokud knihovna DLL odkazovaného typu neobsahuje žádné nativní konstrukce a všechny její závislosti neobsahují žádné nativní konstrukce, zavaděč Windows není vyžadován pro načtení sestavení .NET odkazovaného typu. Kromě toho je možné, že požadované sestavení nebo jeho smíšené nativní/. .NET závislosti již byly načteny jiným kódem. V důsledku toho může být zablokování obtížné odhadnout a může se lišit v závislosti na konfiguraci cílového počítače.

- Za druhé, při načítání knihoven DLL ve verzích 1,0 a 1,1 .NET Framework modul CLR předpokládá, že zámek zavaděče nebyl držen a provede několik akcí, které jsou v uzamknutí zavaděče neplatné. Za předpokladu, že zámek zavaděče není držen, je platný předpoklad pro čistě knihovny DLL rozhraní .NET, ale vzhledem k tomu, že smíšené knihovny DLL spouštějí nativní inicializační rutiny, vyžadují nativní zavaděč systému Windows, a proto je zámek zavaděče. V důsledku toho i v případě, že se vývojář při inicializaci knihovny DLL nepokouší spustit žádné funkce jazyka MSIL, byla stále malá možnost nedeterministického zablokování s verzemi 1,0 a 1,1 .NET Framework.

Všechny jiné než determinismem byly odebrány z smíšeného procesu načítání knihovny DLL. Tyto změny byly provedeny:

- Modul CLR již nevytváří nepravdivé předpoklady při načítání smíšených knihoven DLL.

- Nespravovaná a spravovaná inicializace se provádí ve dvou samostatných a samostatných fázích. K nespravované inicializaci dochází nejprve (přes DllMain) a spravovaná inicializace probíhá poté prostřednictvím. Konstrukce podporovaná `.cctor` .NET. Ta je zcela transparentní pro uživatele, pokud se nepoužívají **/zl** nebo **/NODEFAULTLIB** . Další informace najdete v tématu[/NODEFAULTLIB (ignoruje knihovny)](../build/reference/nodefaultlib-ignore-libraries.md) a [/zl (vynechání názvu výchozí knihovny)](../build/reference/zl-omit-default-library-name.md) .

Zámek zavaděče může stále nastat, ale nyní k němu dochází reproducibly a byl zjištěn. Pokud `DllMain` obsahuje instrukce jazyka MSIL, kompilátor generuje upozornění [kompilátoru upozornění (úroveň 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Kromě toho se buď CRT, nebo modul CLR pokusí rozpoznat a ohlásit pokusy o spuštění MSIL v rámci zámku zavaděče. Při detekci CRT dojde k chybě běhové diagnostiky C R6033.

Zbývající část tohoto dokumentu popisuje zbývající scénáře, pro které lze jazyk MSIL spustit pod zámkem zavaděče, řešení problému v každém z těchto scénářů a techniky ladění.

## <a name="scenarios-and-workarounds"></a>Scénáře a alternativní řešení

Existuje několik různých situací, kdy uživatelský kód může spustit MSIL v uzamknutí zavaděče. Vývojář musí zajistit, aby implementace kódu uživatele neprováděla při každém z těchto okolností instrukce jazyka MSIL. Následující pododdíly popisují všechny možnosti a diskuzi o tom, jak řešit problémy v nejběžnějších případech.

### <a name="dllmain"></a>DllMain

`DllMain` Funkce je uživatelem definovaný vstupní bod pro knihovnu DLL. Pokud uživatel neurčí jinak, `DllMain` je vyvolána pokaždé, když se proces nebo vlákno připojí nebo odpojí z obsahující knihovny DLL. Vzhledem k tomu, že k tomuto vyvolání může dojít, když je držen zámek zavaděče `DllMain` , žádná uživatelem zadaná funkce by neměla být zkompilována do jazyka MSIL. Kromě toho není k dispozici žádná funkce ve stromové `DllMain` struktuře volání v kořenovém adresáři v jazyce MSIL. Chcete-li vyřešit problémy, je třeba změnit blok `DllMain` kódu, který definuje, `unmanaged`pomocí #pragma. Stejné by měly být provedeny pro všechny funkce, `DllMain` které volají.

V případech, kdy tyto funkce musí volat funkci, která vyžaduje implementaci MSIL pro jiné volající kontexty, lze použít strategii duplikace, kde jsou vytvořeny rozhraní .NET i nativní verze stejné funkce.

Případně, pokud `DllMain` není vyžadován nebo pokud není nutné provádět v rámci uzamknutí zavaděče, lze odebrat uživatelem zadanou `DllMain` implementaci, čímž dojde k odstranění problému.

Pokud se DllMain pokusí spustit jazyk MSIL přímo, bude výsledkem [Upozornění kompilátoru (úroveň 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) . Kompilátor ale nemůže detekovat případy, kdy DllMain volá funkci v jiném modulu, který se zase pokusí spustit jazyk MSIL.

Další informace o tomto scénáři naleznete v tématu [překážky pro diagnostiku](#impediments-to-diagnosis).

### <a name="initializing-static-objects"></a>Inicializace statických objektů

Inicializace statických objektů může vést k zablokování, pokud je požadován dynamický inicializátor. Pro jednoduché případy, například pokud je statická proměnná přiřazena k hodnotě známé v době kompilace, není nutná žádná dynamická inicializace, takže nedochází k zablokování. Statické proměnné inicializované voláním funkce, vyvolání konstruktoru nebo výrazy, které nelze vyhodnotit v době kompilace, však vyžadují, aby při inicializaci modulu běžel kód.

Následující kód ukazuje příklady statických inicializátorů, které vyžadují dynamickou inicializaci: volání funkce, konstrukce objektu a inicializace ukazatele. (Tyto příklady nejsou statické, ale jsou považovány za definované v globálním oboru, který má stejný efekt.)

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

Toto riziko zablokování závisí na tom, zda obsažený modul je zkompilován s možností **/CLR** a zda bude zpracováno MSIL. Konkrétně, pokud je statická proměnná zkompilována bez **/CLR** (nebo se nachází v bloku #pragma `unmanaged` ), a dynamický inicializátor vyžadovaný k jeho inicializaci má za následek spuštění instrukcí jazyka MSIL, může dojít k zablokování. Je to proto, že pro moduly zkompilované bez **/CLR**je inicializace statických proměnných prováděna v DllMain. Naproti tomu statické proměnné zkompilované s **/CLR** jsou inicializovány pomocí `.cctor`, po dokončení nespravované fáze inicializace a uvolnění zámku zavaděče.

Existuje mnoho řešení pro zablokování způsobené dynamickou inicializací statických proměnných (uspořádané přibližně v čase potřebném k vyřešení problému):

- Zdrojový soubor obsahující statickou proměnnou lze zkompilovat pomocí **/CLR**.

- Všechny funkce, které jsou volány statickou proměnnou, mohou být zkompilovány do nativního kódu pomocí direktivy #pragma `unmanaged` .

- Ručně naklonujte kód, na kterém závisí statická proměnná, a poskytněte rozhraní .NET i nativní verzi s různými názvy. Vývojáři pak mohou zavolat nativní verzi z nativních statických inicializátorů a zavolat verzi rozhraní .NET jinam.

### <a name="user-supplied-functions-affecting-startup"></a>Uživatelem zadané funkce ovlivňující spuštění

K dispozici je několik uživatelem zadaných funkcí, ve kterých jsou knihovny závislé na inicializaci během spuštění. Například při globálně C++ Přetěžování operátorů v `new` , jako jsou operátory a `delete` , jsou uživatelem zadané verze použity všude, včetně inicializace a zničení C++ standardní knihovny. V důsledku toho C++ budou standardní knihovny a uživatelem zadané statické inicializátory volat všechny uživatelem zadané verze těchto operátorů.

Pokud jsou uživatelem zadané verze zkompilovány do jazyka MSIL, pak se tyto inicializátory pokusí spustit instrukce jazyka MSIL v době, kdy je držen zámek zavaděče. Zadaný `malloc` uživatel má stejné důsledky. Chcete-li vyřešit tento problém, jakékoli z těchto přetížení nebo uživatelsky dodaných definic musí být implementovány jako nativní kód `unmanaged` pomocí direktivy #pragma.

Další informace o tomto scénáři naleznete v tématu [překážky pro diagnostiku](#impediments-to-diagnosis).

### <a name="custom-locales"></a>Vlastní národní prostředí

Pokud uživatel zadá vlastní globální národní prostředí, bude toto národní prostředí použito pro inicializaci všech budoucích vstupně-výstupních proudů, včetně datových proudů, které jsou staticky inicializovány. Pokud je tento globální objekt národního prostředí zkompilován do jazyka MSIL, pak mohou být členské funkce národního objektu kompilovány do jazyka MSIL vyvolány v době, kdy je držen zámek zavaděče.

Existují tři možnosti pro řešení tohoto problému:

Zdrojové soubory obsahující všechny globální vstupně-výstupní proudové definice mohou být kompilovány pomocí možnosti **/CLR** . Zabraňuje jejich statickému inicializátoru v provádění uzamknutí zavaděče.

Definice funkce vlastního národního prostředí lze zkompilovat do nativního kódu pomocí direktivy #pragma `unmanaged` .

Nepoužívejte možnost nastavit vlastní národní prostředí jako globální národní prostředí, dokud se neuvolní zámek zavaděče. Potom explicitně nakonfigurujte vstupně-výstupní proudy vytvořené během inicializace pomocí vlastního národního prostředí.

## <a name="impediments-to-diagnosis"></a>Překážky pro diagnostiku

V některých případech je obtížné zjistit zdroj zablokování. Následující pododdíly projednávají tyto scénáře a způsoby, jak tyto problémy obejít.

### <a name="implementation-in-headers"></a>Implementace v hlavičkách

V rámci výběrových případů mohou implementace funkcí uvnitř hlavičkových souborů zkomplikovat diagnostiky. Vložené funkce a kód šablony vyžadují, aby byly v hlavičkovém souboru zadány funkce.  C++ Jazyk určuje jedno pravidlo definice, které vynutí sémantickou shodu všech implementací funkcí se stejným názvem. V C++ důsledku toho linker nemusí při slučování souborů objektů, které mají duplicitní implementace dané funkce, dělat žádné zvláštní požadavky.

Před verzí sady Visual Studio 2005 linker jednoduše zvolí největší z těchto sémantickě ekvivalentních definic, aby vyhověly dopředné deklarace a scénáře, kdy se pro různé zdrojové soubory používají různé možnosti optimalizace. Vytvoří problém pro smíšené nativní/. NET knihovny DLL.

Vzhledem k tomu, že stejná hlavička může být C++ zahrnuta jak pomocí souborů s možností **/CLR** Enabled a disabled, nebo může být `#pragma unmanaged` #include zabalena uvnitř bloku, je možné mít jazyk MSIL i nativní verze funkcí, které poskytují implementace v záhlaví. Jazyk MSIL a nativní implementace mají odlišnou sémantiku s ohledem na inicializaci pod zámkem zavaděče, což efektivně porušuje pravidlo jednoho definice. Proto když linker zvolí největší implementaci, může zvolit verzi jazyka MSIL funkce, i když byla explicitně zkompilována do nativního kódu jinde pomocí #pragma nespravované direktivy. Aby se zajistilo, že verze jazyka MSIL šablony nebo vložené funkce se nikdy nevolá v rámci zámku zavaděče, musí se každá definice každé takové funkce, která je volána `#pragma unmanaged` v uzamknutí zavaděče, upravovat pomocí direktivy. Pokud je hlavičkový soubor od třetí strany, nejjednodušší způsob, jak tuto změnu provést, je nasdílení a `#pragma unmanaged` vložení direktivy do této direktivy #include pro problematický soubor hlaviček. (Příklad najdete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md) .) Tato strategie ale nebude fungovat pro hlavičky, které obsahují jiný kód, který musí přímo volat rozhraní API .NET.

Pro uživatele, kteří se zabývat zámky zavaděče, linker zvolí nativní implementaci prostřednictvím spravovaného kódu, pokud je k dispozici v obou. Toto výchozí nastavení zabrání výše uvedeným problémům. Existují však dvě výjimky z tohoto pravidla v této verzi z důvodu dvou nevyřešených problémů s kompilátorem:

- Volání vložené funkce je prostřednictvím globálního ukazatele na statických funkcích. Tento scénář je významný, protože virtuální funkce jsou volány prostřednictvím ukazatelů globálních funkcí. Například

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

### <a name="diagnosing-in-debug-mode"></a>Diagnostikování v režimu ladění

Všechny diagnostiky problémů uzamknutí zavaděče by měly být provedeny pomocí sestavení ladění. Sestavení vydaných verzí nemusí způsobovat diagnostiku a optimalizace provedené v režimu vydání mohou maskovat některé z MSIL v rámci scénářů uzamknutí zavaděče.

## <a name="how-to-debug-loader-lock-issues"></a>Jak ladit problémy s zámkem zavaděče

Diagnostika, kterou modul CLR generuje, když je vyvolána funkce jazyka MSIL, způsobí, že modul CLR pozastaví provádění. To zase způsobí, že se ladicí C++ program v kombinaci se smíšeným režimem pozastaví i při spuštění laděného procesu v procesu. Když se ale připojíte k procesu, není možné získat spravované zásobník volání pro laděného procesu pomocí kombinovaného ladicího programu.

Chcete-li identifikovat konkrétní funkci jazyka MSIL, která byla volána v rámci zámku zavaděče, vývojáři by měli provést následující kroky:

1. Zajistěte, aby byly k dispozici symboly pro mscoree. dll a knihovny Mscorwks. dll.

   Symboly můžete nastavit dvěma způsoby. Nejprve lze do cesty pro hledání symbolů přidat soubory PDB pro mscoree. dll a knihovny Mscorwks. dll. Pokud je chcete přidat, otevřete dialogové okno Možnosti cesty hledání symbolů. (V nabídce **nástroje** klikněte na příkaz **Možnosti**. V levém podokně dialogového okna **Možnosti** otevřete uzel **ladění** a vyberte možnost **symboly**.) Přidejte cestu do souborů Mscoree. dll a knihovny Mscorwks. dll do seznamu hledání. Tyto soubory PDB jsou nainstalovány do%VSINSTALLDIR%\SDK\v2.0\symbols. Zvolte **OK**.

   Za druhé se soubory PDB pro mscoree. dll a knihovny Mscorwks. dll dají stáhnout ze serveru symbolů Microsoftu. Chcete-li nakonfigurovat server symbolů, otevřete dialogové okno Možnosti cesty hledání symbolů. (V nabídce **nástroje** klikněte na příkaz **Možnosti**. V levém podokně dialogového okna **Možnosti** otevřete uzel **ladění** a vyberte možnost **symboly**.) Přidejte tuto cestu hledání do seznamu hledání: `https://msdl.microsoft.com/download/symbols`. Přidejte adresář mezipaměti symbolů do textového pole mezipaměť serveru symbolů. Zvolte **OK**.

1. Nastavte režim ladicího programu na režim pouze nativní.

   Otevřete mřížku **vlastností** pro spouštěný projekt v řešení. Vyberte možnosti **Konfigurace** > **ladění**. Nastavte **Typ ladicího programu** na **pouze nativní**.

1. Spusťte ladicí program (F5).

1. Když je vygenerována Diagnostika **/CLR** , zvolte možnost **Opakovat** a pak zvolte možnost přerušit.

1. Otevřete okno zásobník volání. (Na panelu nabídek vyberte možnost **ladit** > **zásobník volání** **systému Windows** > .) Problematický `DllMain` nebo statický inicializátor je identifikován zelenou šipkou. Pokud není zjištěna problematická funkce, je nutné provést následující kroky, aby je bylo možné najít.

1. Otevřete okno **Immediate** (na panelu nabídek vyberte možnost**okamžitě** **ladit** > **Windows** > ).

1. Zadejte `.load sos.dll` do příkazového **podokna** pro načtení služby SOS Debugging Service.

1. Zadejte `!dumpstack` do příkazového **podokna** , abyste získali úplný seznam interní sady **/CLR** .

1. Vyhledá první instanci (nejbližší k dolnímu okraji zásobníku) buď _CorDllMain (Pokud `DllMain` způsobuje problém), nebo _VTableBootstrapThunkInitHelperStub nebo GetTargetForVTableEntry (Pokud se problém vyřeší pomocí statického inicializátoru). Položka zásobníku, která je bezprostředně pod tímto voláním, je vyvolání implementované funkce jazyka MSIL, která se pokusila provést v uzamknutí zavaděče.

1. V předchozím kroku přejdete na zdrojový soubor a číslo řádku a opravte problém pomocí scénářů a řešení popsaných v části scénáře.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje, jak se vyhnout uzamknutí zavaděče přesunutím `DllMain` kódu z do konstruktoru globálního objektu.

V této ukázce je globální spravovaný objekt, jehož konstruktor obsahuje spravovaný objekt, který byl původně v `DllMain`. Druhá část této ukázky odkazuje na sestavení, vytvoření instance spravovaného objektu pro vyvolání konstruktoru modulu, který provede inicializaci.

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

Tento příklad ukazuje problémy při inicializaci smíšených sestavení:

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

Tento kód generuje následující výstup:

```Output
Module ctor initializing based on global instance of class.

Test called so linker does not throw away unused object.
```

## <a name="see-also"></a>Viz také:

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
