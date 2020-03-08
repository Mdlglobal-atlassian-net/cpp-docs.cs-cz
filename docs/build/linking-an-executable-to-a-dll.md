---
title: Propojení spustitelného souboru s knihovnou DLL
ms.date: 08/22/2019
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
ms.openlocfilehash: 2f907fedcaaf9897749ee0eb6a7ea5a33e1af679
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856823"
---
# <a name="link-an-executable-to-a-dll"></a>Propojení spustitelného souboru s knihovnou DLL

Spustitelný soubor odkazuje na (nebo načítá) knihovnu DLL jedním ze dvou způsobů:

- *Implicitní propojení*, kde operační systém načte knihovnu DLL ve stejnou dobu jako spustitelný soubor, který ho používá. Klientský spustitelný soubor volá exportované funkce knihovny DLL stejným způsobem jako v případě, že byly funkce staticky propojeny a obsaženy ve spustitelném souboru. Implicitní propojení se někdy označuje jako *statické zatížení* nebo *dynamické propojení při načítání*.

- *Explicitní propojování*, kde operační systém načte knihovnu DLL na vyžádání za běhu. Spustitelný soubor, který používá knihovnu DLL explicitním propojením, musí explicitně načíst a uvolnit knihovnu DLL. Také musí nastavit ukazatel na funkci pro přístup ke všem funkcím, které používá z knihovny DLL. Na rozdíl od volání funkcí v staticky propojené knihovně nebo implicitně propojené knihovně DLL musí klientský spustitelný soubor volat exportované funkce v explicitně propojené knihovně DLL prostřednictvím ukazatelů na funkce. Explicitní propojování se někdy označuje jako dynamické *načítání* nebo *dynamické propojení run-time*.

Spustitelný soubor může použít buď metodu propojení, pro propojení se stejnou knihovnou DLL. Kromě toho tyto metody nejsou vzájemně exkluzivní; jeden spustitelný soubor se může implicitně propojit s knihovnou DLL a druhý se k němu může připojit explicitně.

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>Určete, kterou propojovací metodu použít

Zda se má použít implicitní nebo explicitní propojení, je rozhodování o architektuře, které je nutné provést pro svou aplikaci. Existují výhody a nevýhody jednotlivých metod.

### <a name="implicit-linking"></a>Implicitní propojení

Implicitní propojení nastane, pokud kód aplikace volá exportovanou funkci DLL. Když je zdrojový kód volajícího spustitelného souboru zkompilován nebo sestaven, volání funkce knihovny DLL generuje odkaz na externí funkci v kódu objektu. Chcete-li tento externí odkaz vyřešit, musí aplikace propojit s knihovnou import (soubor. lib), kterou poskytl tvůrce knihovny DLL.

Knihovna importů obsahuje pouze kód pro načtení knihovny DLL a k implementaci volání funkcí v knihovně DLL. Hledání externí funkce v knihovně importu informuje linker, že kód této funkce je v knihovně DLL. Chcete-li přeložit externí odkazy na knihovny DLL, linker jednoduše přidá informace do spustitelného souboru, který oznamuje systému, kde najít kód knihovny DLL při spuštění procesu.

Když systém spustí program, který obsahuje dynamicky propojené odkazy, použije informace ve spustitelném souboru programu k vyhledání požadovaných knihoven DLL. Pokud knihovna DLL nenajde, systém ukončí proces a zobrazí dialogové okno, které hlásí chybu. V opačném případě systém mapuje moduly DLL do adresního prostoru procesu.

Pokud má kterákoli z knihoven DLL funkci vstupního bodu pro inicializaci a ukončovací kód, jako je například `DllMain`, operační systém zavolá funkci. Jeden z parametrů předaných funkci vstupního bodu Určuje kód, který označuje, že se knihovna DLL připojuje k procesu. Pokud funkce vstupního bodu nevrátí hodnotu TRUE, systém ukončí proces a ohlásí chybu.

Nakonec systém upraví spustitelný kód procesu tak, aby poskytoval počáteční adresy pro funkce knihovny DLL.

Podobně jako zbytek kódu programu, zavaděč mapuje kód knihovny DLL do adresního prostoru procesu při spuštění procesu. Operační systém ho načte do paměti pouze v případě potřeby. V důsledku toho atributy kódu `PRELOAD` a `LOADONCALL` používané soubory. def k řízení načítání v předchozích verzích systému Windows již nemají význam.

### <a name="explicit-linking"></a>Explicitní propojování

Většina aplikací používá implicitní propojení, protože je nejjednodušší metoda propojování, kterou je potřeba použít. Existují však situace, kdy je nutné explicitní propojení. Tady jsou některé běžné důvody pro použití explicitního propojení:

- Aplikace neznáte název knihovny DLL, kterou načte, až do doby běhu. Například aplikace může získat název knihovny DLL a exportovaných funkcí z konfiguračního souboru při spuštění.

- Proces, který používá implicitní propojení, je ukončen operačním systémem, pokud se knihovna DLL nenajde při spuštění procesu. Proces, který používá explicitní propojování, není v této situaci ukončený a může se pokusit o zotavení z chyby. Proces může například uživateli oznamovat chybu a nechat si zadat jinou cestu ke knihovně DLL.

- Proces, který používá implicitní propojení, je ukončen také v případě, že některá z knihoven DLL, se kterými je propojena, má funkci `DllMain`, která se nezdařila. Proces, který používá explicitní propojování, není v této situaci ukončen.

- Aplikace, která implicitně odkazuje na mnoho knihoven DLL, může být pomalá, protože systém Windows načítá všechny knihovny DLL při načtení aplikace. Pro zlepšení výkonu při spuštění může aplikace použít pouze implicitní propojování pro knihovny DLL vyžadované ihned po načtení. Může použít explicitní propojení k načtení jiných knihoven DLL pouze v případě potřeby.

- Explicitní propojování eliminuje nutnost propojení aplikace pomocí knihovny importů. Pokud změny v knihovně DLL způsobí změnu pořadí exportu, aplikace nebudou muset znovu propojovat, pokud volají `GetProcAddress` pomocí názvu funkce a nikoli pořadovým číslem. Aplikace, které používají implicitní propojení, musí stále znovu připojit ke změněné knihovně importu.

Tady jsou dvě rizika explicitního propojení, na které byste měli vědět:

- Pokud má knihovna DLL funkci vstupního bodu `DllMain`, operační systém zavolá funkci v kontextu vlákna, které se nazývá `LoadLibrary`. Funkce vstupního bodu není volána, pokud je již knihovna DLL připojena k procesu z důvodu předchozího volání `LoadLibrary`, které nemá žádné odpovídající volání funkce `FreeLibrary`. Explicitní propojování může způsobit problémy, pokud knihovna DLL používá funkci `DllMain` k inicializaci každého vlákna procesu, protože všechna vlákna, která již existují při volání `LoadLibrary` (nebo `AfxLoadLibrary`), nejsou inicializována.

- Pokud knihovna DLL deklaruje statická velikost dat jako `__declspec(thread)`, může při explicitním propojení způsobit chybu ochrany. Poté, co je knihovna DLL načtena voláním `LoadLibrary`, způsobí chyba ochrany vždy, když kód odkazuje na tato data. (Statická velikost dat zahrnuje globální i místní statické položky.) To je důvod, proč při vytváření knihovny DLL byste se měli vyhnout použití úložiště místního vlákna. Pokud nemůžete, informujte uživatele knihovny DLL o potenciálním nástrahi dynamického načítání vaší knihovny DLL. Další informace najdete v tématu [použití Thread localho úložiště v dynamické knihovně (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>Používání implicitního propojení

Chcete-li použít knihovnu DLL implicitním propojením, klientské spustitelné soubory musí získat tyto soubory od poskytovatele knihovny DLL:

- Jeden nebo více hlavičkových souborů (soubory. h), které obsahují deklarace exportovaných dat, funkcí a C++ tříd v knihovně DLL. Třídy, funkce a data exportovaná knihovnou DLL musí být označeny `__declspec(dllimport)` v hlavičkovém souboru. Další informace naleznete v tématu [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Knihovna importu, která se má propojit s vaším spustitelným souborem. Linker vytvoří knihovnu importu při sestavení knihovny DLL. Další informace naleznete v tématu [soubory LIB jako vstup linkeru](reference/dot-lib-files-as-linker-input.md).

- Skutečný soubor DLL.

Chcete-li použít data, funkce a třídy v knihovně DLL implicitním propojením, všechny zdrojové soubory klienta musí zahrnovat hlavičkové soubory, které je deklaruje. Z perspektivy kódování jsou volání exportovaných funkcí stejná jako jakákoli jiná volání funkce.

Chcete-li vytvořit klientský spustitelný soubor, je nutné propojit knihovnu import knihovny DLL. Použijete-li externí soubor pravidel nebo sestavovací systém, určete knihovnu importu společně s jinými soubory objektů nebo knihovnami, které jsou propojeny.

Operační systém musí být schopný najít soubor DLL při načtení volajícího spustitelného souboru. To znamená, že je nutné buď nasadit nebo ověřit existenci knihovny DLL při instalaci aplikace.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Postup pro explicitní propojení s knihovnou DLL

Chcete-li použít knihovnu DLL explicitním propojením, aplikace musí provést volání funkce pro explicitní načtení knihovny DLL v době běhu. Pro explicitní propojení s knihovnou DLL musí aplikace:

- Zavolejte [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) nebo podobnou funkci pro načtení knihovny DLL a získání obslužné rutiny modulu.

- Volání [GetProcAddress](getprocaddress.md) pro získání ukazatele funkce na každou exportovanou funkci, kterou aplikace volá. Vzhledem k tomu, že aplikace volají funkce knihovny DLL přes ukazatel, kompilátor negeneruje externí odkazy, takže není nutné propojení s knihovnou import. Je však nutné mít příkaz `typedef` nebo `using`, který definuje podpis volání exportovaných funkcí, které voláte.

- Při práci s knihovnou DLL volejte [FreeLibrary](freelibrary-and-afxfreelibrary.md) .

Například Tato ukázková funkce volá `LoadLibrary` pro načtení knihovny DLL s názvem "MyDLL", volání `GetProcAddress` k získání ukazatele na funkci nazvanou "DLLFunc1", volá funkci a uloží výsledek a poté volá `FreeLibrary` pro uvolnění knihovny DLL.

```C
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)
{
    HINSTANCE hDLL;               // Handle to DLL
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
    HRESULT hrReturnVal;

    hDLL = LoadLibrary("MyDLL");
    if (NULL != hDLL)
    {
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");
        if (NULL != lpfnDllFunc1)
        {
            // call the function
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);
        }
        else
        {
            // report the error
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }
    return hrReturnVal;
}
```

Na rozdíl od tohoto příkladu, ve většině případů byste měli volat `LoadLibrary` a `FreeLibrary` pouze jednou v aplikaci pro danou knihovnu DLL. To je obzvláště true, pokud budete volat více funkcí v knihovně DLL nebo opakovaně volat funkce knihovny DLL.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Práce s knihovnami importu a soubory exportu](reference/working-with-import-libraries-and-export-files.md)

- [Pořadí hledání dynamických propojených knihoven](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Viz také

[Vytváření C/C++ knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md)
