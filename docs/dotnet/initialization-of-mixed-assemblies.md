---
title: "Inicializace smíšených sestavení | Microsoft Docs"
ms.custom: 
ms.date: 03/09/2018
ms.technology:
- cpp-windows
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c4d569987c20a962b0cecf22cd6888b22c920fb5
ms.sourcegitcommit: eb246547c7c9adc7d7ac4083ef09bf6e54dec914
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2018
---
# <a name="initialization-of-mixed-assemblies"></a>Inicializace smíšených sestavení

Vývojáři Windows musí být opatrní u zámek zavaděče při spuštění kódu při `DllMain`. Existuje však několik dalších důležitých informací, které se vyskytnou se při plánování práce s C + +/ sestavení clr ve smíšeném režimu.

Kód v rámci [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) nesmí přístup k modulu CLR. To znamená, že `DllMain` by měly volat žádné spravované funkce, přímo nebo nepřímo; bez spravovaného kódu by měla být deklarován nebo implementované v `DllMain`; a žádné uvolňování paměti nebo automatické načítání knihovna se uskuteční v rámci `DllMain` .
  
## <a name="causes-of-loader-lock"></a>Příčiny zámek zavaděče

Se zavedením platformy .NET jsou dvě odlišné mechanismy pro načítání modul provádění (EXE nebo DLL): jeden pro Windows, který se používá pro nespravované moduly, a jeden pro rozhraní .NET CLR Common Language Runtime (), který načte sestavení .NET. Smíšený problém načtení knihovny DLL se soustředí kolem zavaděč operačního systému Microsoft Windows.

Pokud je sestavení obsahující pouze konstrukce .NET načtené do procesu, zavaděč CLR lze provést všechny potřebné úkoly, načítání a inicializace sám sebe. Však pro smíšená sestavení, protože obsahují nativní kód a data, zavaděč systému Windows musíte použít také.

Zavaděč Windows zaručuje, že žádný kód můžete přístupový kód nebo data v této knihovně DLL předtím, než byl inicializován a že žádný kód nemůže redundantně načíst knihovnu DLL při částečné inicializaci. K tomuto účelu zavaděč systému Windows používá proces globální kritické oddíl (často říká "zámek zavaděče"), který brání nezabezpečený přístup při inicializaci modulu. V důsledku toho je proces načítání citlivé na mnoho scénářů classic zablokování. Následující dva scénáře pro smíšená sestavení, zvýšit riziko napadení zablokování:

- První, pokud se uživatelé pokusí spustit funkce zkompilované do převodního jazyka Microsoft (MSIL) při zámek zavaděče (z `DllMain` nebo statické inicializátory, např.), může dojít k zablokování. Podívejte se do které funkce MSIL odkazuje na typ v sestavení, které nebyla načtena. Modul CLR se pokusí automaticky načíst toto sestavení, které můžou vyžadovat blokování na zámek zavaděče zavaděč systému Windows. Vzhledem k tomu, že kód v dřívější části pořadí volání je již blokován zámek zavaděče, výsledky vzájemné zablokování. Ale provádění MSIL pod zámek zavaděče není zaručeno, že dojde k zablokování, ztěžuje tento scénář tak diagnostikovat a opravit. V některých případech například kde obsahuje knihovnu DLL odkazovaného typu žádné nativní konstrukce a všechny jeho závislosti neobsahují žádné nativní konstrukce, Windows zavaděče není vyžadován k načtení sestavení .NET odkazovaného typu. Kromě toho vyžaduje sestavení nebo jeho závislé součásti smíšené nativní/.NET mohou už byly načteny jiným kódem. V důsledku toho vzájemné zablokování může být obtížné odhadnout a může lišit v závislosti na konfiguraci služby cílového počítače.

- Druhý při načítání knihovny DLL v verze 1.0 a 1.1 rozhraní .NET Framework, modul CLR předpokládá, že aby zámek zavaděče nebyl uchovávat a provést několik akcí, které jsou neplatné v zavaděči. Za předpokladu, že není uchováno zámek zavaděče je platný předpokladů pro čistě knihovny DLL rozhraní .NET, ale protože smíšených knihoven DLL spuštění rutiny nativní inicializace, vyžadují nativní zavaděč systému Windows a proto zámek zavaděče. V důsledku toho i v případě, že vývojář nebyl pokusu o spuštění jakékoli funkce MSIL během inicializace knihovny DLL, se stále malá možnost nedeterministická zablokování pomocí verze 1.0 a 1.1 rozhraní .NET Framework.

Všechny nedeterminismy byla odebrána z procesu načítání smíšených knihoven DLL. To bylo provedeno pomocí tyto změny:

- Modul CLR již neprování chybné předpoklady při načítání smíšených knihoven DLL.

- A nespravované inicializace probíhá ve dvou fázích samostatné a distinct. Nespravovaná inicializace probíhá nejprve (prostřednictvím DllMain) a spravovaná inicializace probíhá později, prostřednictvím. Podporované NET konstrukce názvem *.cctor*. K tomu je pro uživatele zcela transparentní Pokud **/Zl** nebo **/NODEFAULTLIB** se používají. V tématu[/NODEFAULTLIB (Ignorovat knihovny)](../build/reference/nodefaultlib-ignore-libraries.md) a [/Zl (vypuštění název výchozí knihovny)](../build/reference/zl-omit-default-library-name.md) Další informace.

Zámek zavaděče může stále dojít, ale nyní dojde reprodukovaně a je zjištěn. Pokud `DllMain` obsahuje pokyny MSIL kompilátor vygeneruje upozornění [upozornění kompilátoru (úroveň 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Kromě toho CRT nebo CLR se pokusí zjistit a ohlásit pokusy o provedení MSIL v zavaděči. Detekce CRT výsledky za běhu diagnostiky C Run-Time chyby R6033 jazyka.

Zbývající část tohoto dokumentu popisuje scénáře zbývající, pro které můžete provést MSIL pod zámek zavaděče řešení problému v každém z těchto scénářů a techniky ladění.

## <a name="scenarios-and-workarounds"></a>Scénáře a řešení

Existuje několik různých situací, za kterých může uživatel provést kód MSIL v zavaděči. Vývojář musí zajistit, že implementaci kódu uživatele nebude pokoušet provést MSIL pokyny v každém z těchto okolností. Následující témata popisují všechny možnosti s diskuzi o tom, jak vyřešit problémy v nejběžnější případy.

### <a name="dllmain"></a>DllMain

`DllMain` Funkce je uživatelem definované vstupní bod pro knihovny DLL. Pokud uživatel zadá, jinak hodnota `DllMain` je volána pokaždé, když proces nebo podproces nebo odebrání z obsahující DLL Knihovny. Vzhledem k tomu, že toto volání může dojít při zámek zavaděče, ne uživatelem zadané `DllMain` funkce by měl být zkompilovány do MSIL. Kromě toho se žádná funkce ve stromové struktuře volání root na `DllMain` mohou být zkompilovány do MSIL. K vyřešení problémů, bloku kódu, který definuje `DllMain` by měl být upraven s #pragma `unmanaged`. Stejné by mělo být provedeno pro každý funkce, `DllMain` volání.

V případech, kdy musí tyto funkce volání funkce, která vyžaduje implementace MSIL pro další kontexty volání lze použít strategie duplikace kde jsou vytvářeny .NET a nativní verzi stejné funkce.

Případně pokud `DllMain` není nutné nebo pokud ji není nutné provést v rámci zavaděč uzamknout, zadaný uživatelem `DllMain` lze odebrat implementace, které odstraní problém.

Pokud DllMain pokusí spustit MSIL přímo, [upozornění kompilátoru (úroveň 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) způsobí. Kompilátor však nelze rozpoznat případech, kde DllMain volá funkci v jiný modul, který naopak se pokusí spustit MSIL.

Další informace o tomto scénáři najdete v části "Překážky pro diagnostiku".

### <a name="initializing-static-objects"></a>Inicializace statických objektů

Inicializace statických objektů může způsobit zablokování, pokud je potřeba inicializátoru dynamické. Pro jednoduché případech, například když je statická proměnná jednoduše přiřadit hodnotu známé v době kompilace žádné dynamické inicializace je nutné, aby riziko vzájemného zablokování. Statické proměnné inicializuje pomocí volání funkce, volání konstruktoru nebo výrazy, které nelze vyhodnotit během kompilace však čas všechny vyžadují kód pro spuštění při inicializaci modulu.

Následující kód ukazuje příklady statické inicializátory, které vyžadují dynamické inicializace: volání funkce, vytváření objektů a inicializace ukazatele. (Tyto příklady nejsou statické, ale se předpokládá, že být definován v globálním oboru, který má stejný účinek.)

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

Toto riziko vzájemného zablokování závisí na tom, jestli je modul obsahující kompilovat s **/CLR** a zda bude proveden MSIL. Konkrétně Pokud statické proměnné je kompilovat bez **/CLR** (nebo se nachází v #pragma `unmanaged` bloku), a je potřeba provést jeho inicializaci výsledky ve spuštění MSIL pokyny dynamické inicializace, může dojít k zablokování. Důvodem je, že pro moduly zkompilované bez **/CLR**, inicializace statické proměnné provádí zpracování funkce DllMain. Naproti tomu statické proměnné kompilovat s **/CLR** jsou iniciovány .cctor po dokončení nespravované inicializační fázi a zámek zavaděče byla uvolněna.

Existuje několik řešení pro zablokování způsobené dynamickou inicializaci statické proměnné (uspořádány přibližně v pořadí podle doby nutné k vyřešení problému):

- Zdrojový soubor obsahující statickou proměnnou můžete kompilovat s **/CLR**.

- Všechny funkce, které jsou volány statické proměnné mohou být zkompilovány do nativního kódu pomocí #pragma `unmanaged` – direktiva.

- Ručně zkopírujte kód, který statické proměnné závisí na, poskytuje .NET a nativní verzi s různými názvy. Vývojářům můžete volat nativní verzi z nativní statické inicializátory a jinde volat verze rozhraní .NET.

### <a name="user-supplied-functions-affecting-startup"></a>Uživatelem zadané funkce, které mají vliv na spuštění

Jsou několik uživatelem zadané funkce, na kterých závisí knihovny pro inicializaci během spouštění. Například při globálním přetížení operátorů v jazyce C++, jako `new` a `delete` operátory, uživatelské verze slouží všude, včetně inicializace standardní knihovna C++ a odstranění. Zadaný uživatelem statické inicializátory a standardní knihovna C++ v důsledku toho budou vyvolání jakékoli uživatelské verze těchto operátorů.

Pokud uživatel verze zkompilovány do MSIL, budou tyto inicializátory pokus pro spouštění instrukcí MSIL při uzamčení zavaděče. Uživatelem zadané `malloc` má stejné důsledky. Chcete-li vyřešit tento problém, některé tyto přetížení nebo uživatelem zadané definice musí být implementovány v nativním kódu pomocí #pragma `unmanaged` – direktiva.

Další informace o tomto scénáři najdete v části "Překážky pro diagnostiku".

### <a name="custom-locales"></a>Vlastní národní prostředí

Pokud uživatel poskytuje vlastní globální národní prostředí, toto národní prostředí se použije pro všechny budoucí vstupně-výstupní datové proudy, včetně těch, které jsou inicializovat staticky inicializace. Pokud tento objekt globální národního prostředí zkompilován k MSIL, pak členské funkce objektu národního prostředí zkompilovány do MSIL mohou být vyvolány během uzamčení zavaděče.

Existují tři možnosti pro řešení tohoto problému:

Zdrojové soubory obsahující všechny globální definice datového proudu vstupně-výstupních operací můžete zkompilovat pomocí **/CLR** možnost. To zabrání jejich statické inicializátory z se spouští v zavaděči.

Definice funkcí vlastní národní prostředí může být zkompilovány do nativního kódu pomocí #pragma `unmanaged` – direktiva.

Nepoužívejte nastavení vlastní národní prostředí jako globální národního prostředí až po vydání zámek zavaděče. Potom nakonfigurujte explicitně vstupně-výstupní datové proudy vytvořené během inicializace s vlastní národní prostředí.

## <a name="impediments-to-diagnosis"></a>Překážky pro diagnostiku

V některých případech je obtížné zjistit zdroj vzájemného zablokování. Následující témata popisují tyto scénáře a způsoby, jak vyřešit tyto problémy.

### <a name="implementation-in-headers"></a>Implementace v záhlaví

V případech, vyberte možnost implementace funkce uvnitř soubory hlaviček zkomplikovat diagnostiky. Vložené funkce a kód šablony vyžadují, aby byl specifikován funkce v záhlaví souboru.  Jazyk C++ určuje jedno pravidlo definice, které vynutí všechny implementace funkcí se stejným názvem jako sémanticky rovnocenné. V důsledku toho nemusí linkeru C++ zkontrolujte žádná zvláštní opatření, při slučování objektu souborů, které mají duplicitní implementace dané funkce.

Před Visual Studio 2005 linkeru jednoduše zvolí největší tyto sémanticky ekvivalentní definic, aby bylo možné ošetřit scénáře a předat dál deklarace Pokud možnosti různých optimalizace se používá pro jiné zdrojové soubory. Tím se vytvoří problém pro smíšené nativní/.NET knihovny DLL.

Vzhledem k tomu může být stejná hlavička vložena jak C++ souborů s **/CLR** povolené a zakázané, nebo #include může být uzavřen uvnitř #pragma `unmanaged` bloku, je možné, že MSIL a nativní verze funkcí, které poskytují implementace v záhlaví. MSIL a nativní implementace mají různé sémantiku s ohledem na inicializace pod zámek zavaděče, které efektivně porušuje pravidlo jednu definici. V důsledku toho při linkeru vybere největší implementace, je rozhodnout MSIL verze funkce, i v případě, že jeho explicitně kompilace nativního kódu jinde použitím směrnice #pragma unmanaged. Aby se zajistilo, že verze MSIL šablony nebo vložené funkce je volána nikdy pod zámek zavaděče, musí každá definice každé funkce volána v rámci zámek zavaděče upravena s #pragma `unmanaged` – direktiva. Pokud soubor hlaviček od třetích stran, je nejjednodušší způsob, jak dosáhnout vložit a #pragma – direktiva nespravované kolem #include – direktiva pro problematický soubor hlaviček. (Viz [spravované, nespravované](../preprocessor/managed-unmanaged.md) příklad.) Tato strategie však nebude fungovat pro hlavičky, které obsahují jiný kód, který musí přímo volat rozhraní API technologie .NET.

V zájmu usnadnění pro uživatele zabývající se zámek zavaděče linkeru vybere nativní implementaci před spravovanou při předání obou. Tím je zabráněno uvedené problémy. Nicméně existují dvě výjimky z tohoto pravidla v této verzi z důvodu dvě nevyřešené problémy s překladačem:

- Volání je vložené funkce je prostřednictvím ukazatele globální statické funkce. Tento scénář je zvláště upozorňují na důležité, protože virtuální funkce jsou volány prostřednictvím ukazatelů globální funkce. Například
  
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

Všechny Diagnostika zámek zavaděče, které by mělo být provedeno problémy s ladicí sestavení. Verze sestavení nemohou být diagnostiky a optimalizace provést v režimu vydání mohou maskovat některé MSIL ve scénáři uzamčení zavaděče.

## <a name="how-to-debug-loader-lock-issues"></a>Postup ladění problémů zámek zavaděče

Diagnostika, který generuje modulu CLR při vyvolání funkce MSIL způsobí, že CLR pozastavit provádění. Naopak to způsobí, že ladicí program Visual C++ ve smíšeném režimu pozastaví také pozastaven v-procesu. Ale při připojování k procesu, není možné získat spravované zásobník volání pro ladění, používání smíšený ladicího programu.

Pokud chcete identifikovat konkrétní funkce MSIL, která byla volána v rámci zámek zavaděče, vývojáři provést následující kroky:

1. Ujistěte se, že symboly pro mscoree.dll a mscorwks.dll jsou k dispozici.

   Tento krok můžete provést dvěma způsoby. Soubory PDB pro mscoree.dll a mscorwks.dll nejprve lze přidat do cestu hledání symbolů. K tomu, otevřete dialogové okno Možnosti cesta hledání symbolu. (Z **nástroje** nabídce zvolte **možnosti**. V levém podokně **možnosti** dialogové okno, otevřete **ladění** uzel a zvolte **symboly**.) Přidejte cestu k mscoree.dll a mscorwks.dll soubory PDB do seznamu hledání. Tyto soubory PDB jsou nainstalovány do % VSINSTALLDIR%\SDK\v2.0\symbols. Zvolte **OK**.

   Druhý PDB pro mscoree.dll a mscorwks.dll si můžete stáhnout ze serveru Microsoft Symbol. Konfigurace serveru Symbol, otevřete dialogové okno Možnosti cesta hledání symbolu. (Z **nástroje** nabídce zvolte **možnosti**. V levém podokně **možnosti** dialogové okno, otevřete **ladění** uzel a zvolte **symboly**.) Přidat následující cestu vyhledávání do seznamu hledání: http://msdl.microsoft.com/download/symbols. Přidejte adresář mezipaměti symbol do textového pole symbol server mezipaměti. Zvolte **OK**.

1. Nastavte režim ladění na nativní režim.

   Chcete-li to provést, otevřete **vlastnosti** mřížky pro projekt po spuštění v řešení. Vyberte **vlastnosti konfigurace** > **ladění**. Nastavte **ladicího programu typ** k **pouze nativní**.

1. Spuštění ladicího programu (F5).
  
1. Když **/CLR** diagnostiky se vygeneruje, zvolte **opakujte** a potom vyberte **rozdělit**.
  
1. Otevřete okno zásobník volání. (Na řádku nabídek zvolte **ladění** > **Windows** > **zásobníkem volání**.) Je problematický `DllMain` nebo statický inicializátor je označen zelenou šipku. Pokud není problematická funkce určena, musí se ho najít provedeny následující kroky.

1. Otevřete **Immediate** okno (na řádku nabídek zvolte **ladění** > **Windows** > **Immediate**.)

1. Napište .load sos.dll do **Immediate** k načtení SOS ladění služby.
  
1. Typ! dumpstack do **Immediate** okno získat úplný seznam všech interní **/CLR** zásobníku.

1. Vyhledejte první instance (nejblíže k dolnímu okraji zásobníku) buď _CorDllMain (Pokud `DllMain` způsobí, že problém) nebo _VTableBootstrapThunkInitHelperStub nebo GetTargetForVTableEntry (Pokud inicializátoru statické způsobí, že problém). Záznam zásobníku pod toto volání je že vyvolání MSIL implementovat funkce, která se pokusila provést v zavaděči.

1. Přejděte na zdrojový soubor a číslo zjištěná v předchozím kroku a správnou řádku problém pomocí scénářů a řešení, které jsou popsané v části scénáře.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje, jak se vyhnout zámek zavaděče přesunutím kód z `DllMain` do konstruktoru objektu globální.

V této ukázce je globální spravovaný objekt, jehož konstruktor obsahuje spravovaný objekt, který byl původně v `DllMain`. Druhá část této ukázky odkazuje na sestavení, vytvoření instance spravovaného objektu se vyvolat konstruktor modul, který provede inicializaci.

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

## <a name="see-also"></a>Viz také

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
