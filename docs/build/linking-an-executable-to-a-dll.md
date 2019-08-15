---
title: Propojení spustitelného souboru s knihovnou DLL
ms.date: 11/04/2016
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
ms.openlocfilehash: c4f9ea7a3606612189e85401b75a0577896fd90e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493229"
---
# <a name="link-an-executable-to-a-dll"></a>Propojení spustitelného souboru s knihovnou DLL

Spustitelný soubor odkazuje na (nebo načítá) knihovnu DLL jedním ze dvou způsobů:

- *Implicitní propojení*, kde operační systém knihovnu DLL načte, když je načten spustitelný soubor, který jej používá. Klientský spustitelný soubor volá exportované funkce knihovny DLL stejně, jako kdyby byly funkce staticky propojeny a obsaženy ve spustitelném souboru. Implicitní propojení se někdy označuje jako *statické zatížení* nebo *dynamické propojení při načítání*.

- *Explicitní propojování*, kde operační systém načte knihovnu DLL na vyžádání za běhu. Spustitelný soubor, který používá knihovnu DLL explicitním propojením, musí učinit volání funkce pro explicitní načtení a uvolnění knihovny DLL a pro přístup k funkcím, které jsou exportovány knihovnou DLL. Na rozdíl od volání funkcí ve staticky propojené knihovně musí klientský spustitelný soubor volat exportované funkce v knihovně DLL prostřednictvím ukazatele na funkci. Explicitní propojování se někdy označuje jako dynamické *načítání* nebo *dynamické propojení run-time*.

Spustitelný soubor může použít buď metodu propojení, pro propojení se stejnou knihovnou DLL. Kromě toho tyto metody nejsou vzájemně exkluzivní; jeden spustitelný soubor se může implicitně propojit s knihovnou DLL a druhý se k němu může připojit explicitně.

<a name="determining-which-linking-method-to-use"></a>

## <a name="link-an-executable-to-a-dll"></a>Propojení spustitelného souboru s knihovnou DLL

Zda se má použít implicitní nebo explicitní propojení, je rozhodování o architektuře, které je nutné provést pro svou aplikaci. Existují výhody a nevýhody jednotlivých metod.

### <a name="implicit-linking"></a>Implicitní propojení

Implicitní propojení nastane, pokud kód aplikace volá exportovanou funkci DLL. Když je zdrojový kód volajícího spustitelného souboru zkompilován nebo sestaven, volání funkce knihovny DLL generuje odkaz na externí funkci v kódu objektu. Chcete-li tento externí odkaz vyřešit, musí aplikace propojit s knihovnou import (soubor. lib), kterou poskytl tvůrce knihovny DLL.

Knihovna importů obsahuje pouze kód pro načtení knihovny DLL a k implementaci volání funkcí v knihovně DLL. Hledání externí funkce v knihovně importu informuje linker, že kód této funkce je v knihovně DLL. Chcete-li přeložit externí odkazy na knihovny DLL, linker jednoduše přidá informace do spustitelného souboru, který oznamuje systému, kde najít kód knihovny DLL při spuštění procesu.

Když systém spustí program, který obsahuje dynamicky propojené odkazy, použije informace ve spustitelném souboru programu k vyhledání požadovaných knihoven DLL. Pokud nemůže najít knihovnu DLL, systém ukončí proces a zobrazí dialogové okno, které hlásí chybu. V opačném případě systém mapuje moduly DLL do adresního prostoru procesu.

Pokud má kterákoli z knihoven DLL funkci vstupního bodu pro inicializaci a ukončovací kód `DllMain`, například, operační systém zavolá funkci. Jeden z parametrů předaných funkci vstupního bodu Určuje kód, který označuje, že se knihovna DLL připojuje k procesu. Pokud funkce vstupního bodu nevrátí hodnotu TRUE, systém ukončí proces a ohlásí chybu.

Nakonec systém upraví spustitelný kód procesu tak, aby poskytoval počáteční adresy pro funkce knihovny DLL.

Podobně jako zbytek kódu programu je kód knihovny DLL mapován do adresního prostoru procesu při spuštění procesu a je načten do paměti pouze v případě potřeby. V důsledku toho `PRELOAD` atributy kódu a `LOADONCALL` používané soubory. def k řízení načítání v předchozích verzích systému Windows již nemají význam.

### <a name="explicit-linking"></a>Explicitní propojování

Většina aplikací používá implicitní propojení, protože je nejjednodušší metoda propojování, kterou je možné použít. Existují však situace, kdy je nutné explicitní propojení. Tady jsou některé běžné důvody pro použití explicitního propojení:

- Aplikace neznáte název knihovny DLL, která je načtena do doby běhu. Například aplikace může získat název knihovny DLL a exportovaných funkcí z konfiguračního souboru při spuštění.

- Proces, který používá implicitní propojení, je ukončen operačním systémem, pokud se knihovna DLL nenajde při spuštění procesu. Proces, který používá explicitní propojování, není v této situaci zakončený a může se pokusit o zotavení po chybě. Proces může například uživateli oznamovat chybu a nechat si zadat jinou cestu ke knihovně DLL.

- Proces, který používá implicitní propojení, je ukončen také v `DllMain` případě, že některá z knihoven DLL, ke kterým je propojena, má funkci, která je neúspěšná. Proces, který používá explicitní propojení, není v této situaci ukončen.

- Aplikace, která implicitně odkazuje na mnoho knihoven DLL, může být pomalá, protože systém Windows načítá všechny knihovny DLL při načtení aplikace. Pro zlepšení výkonu při spuštění se aplikace může propojit implicitně pouze s těmito knihovnami DLL, které jsou požadovány ihned po načtení, a počkat, až jiné knihovny DLL budou vyžadovat, aby k nim explicitně propojí.

- Explicitní propojování eliminuje nutnost propojení aplikace pomocí knihovny importů. Pokud změny v knihovně DLL způsobují změnu pořadí exportu, aplikace, které používají explicitní propojení, nemusí znovu propojovat, pokud volají `GetProcAddress` pomocí názvu funkce a nikoliv pořadového čísla, zatímco aplikace, které používají implicitní propojení, musí znovu propojit s Nová knihovna pro import.

Tady jsou dvě rizika explicitního propojení, na které byste měli vědět:

- Pokud má `DllMain` knihovna DLL funkci vstupního bodu, operační systém zavolá funkci v kontextu vlákna, které volalo `LoadLibrary`. Funkce vstupního bodu není volána, je-li již knihovna DLL připojena k procesu z důvodu předchozího volání metody `LoadLibrary` , které nemá odpovídající volání `FreeLibrary` funkce. Explicitní propojování může způsobit problémy, pokud knihovna DLL `DllMain` používá funkci k provedení inicializace pro každé vlákno procesu, protože vlákna, která již existují `LoadLibrary` , pokud `AfxLoadLibrary`je volána metoda (nebo), nejsou inicializována.

- Pokud knihovna DLL deklaruje statická velikost dat jako `__declspec(thread)`, může dojít k chybě ochrany, pokud je explicitně propojena. Poté `LoadLibrary`, co je knihovna DLL načtena voláním, způsobí selhání ochrany vždy, když kód odkazuje na tato data. (Statická velikost dat zahrnuje globální i místní statické položky.) Proto při vytváření knihovny DLL byste se buď vyhnuli použití úložiště místního vlákna, nebo informování uživatelů knihoven DLL o potenciálním nástrahi dynamického načítání vaší knihovny DLL. Další informace najdete v tématu [použití Thread localho úložiště v dynamické knihovně (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="link-an-executable-to-a-dll"></a>Propojení spustitelného souboru s knihovnou DLL

Chcete-li použít knihovnu DLL implicitním propojením, klientské spustitelné soubory musí získat tyto soubory od poskytovatele knihovny DLL:

- Jeden nebo více hlavičkových souborů (soubory. h), které obsahují deklarace exportovaných dat, funkcí a C++ tříd v knihovně DLL. Třídy, funkce a data exportovaná knihovnou DLL musí být označeny `__declspec(dllimport)` v hlavičkovém souboru. Další informace naleznete v tématu [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Knihovna importu, která se má propojit s vaším spustitelným souborem. Linker vytvoří knihovnu importu při sestavení knihovny DLL. Další informace najdete v tématu [. Soubory LIB](reference/dot-lib-files-as-linker-input.md).

- Skutečný soubor DLL.

Chcete-li použít knihovnu DLL implicitním propojením, spustitelný soubor musí obsahovat hlavičkové soubory, které deklaruje data C++ , funkce nebo třídy exportované knihovnou DLL v každém zdrojovém souboru, který obsahuje volání exportovaných dat, funkcí a tříd. Z perspektivy kódování jsou volání exportovaných funkcí stejná jako jakákoli jiná volání funkce.

Chcete-li vytvořit volající spustitelný soubor, je nutné propojit s knihovnou import. Použijete-li externí soubor pravidel nebo sestavovací systém, zadejte název souboru knihovny importu, kde jsou uvedeny jiné soubory objektů (. obj) nebo knihovny, které odkazujete.

Operační systém musí být schopný najít soubor DLL při načtení volajícího spustitelného souboru. To znamená, že aplikace musí nasadit nebo ověřit existenci knihovny DLL při instalaci aplikace.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Postup pro explicitní propojení s knihovnou DLL

Chcete-li použít knihovnu DLL explicitním propojením, aplikace musí provést volání funkce pro explicitní načtení knihovny DLL v době běhu. Pro explicitní propojení s knihovnou DLL musí aplikace:

- Zavolejte [](loadlibrary-and-afxloadlibrary.md)funkci LoadLibrary `LoadLibraryEx`, nebo podobnou funkci pro načtení knihovny DLL a získání popisovače modulu.

- Volání [GetProcAddress](getprocaddress.md) pro získání ukazatele funkce na každou exportovanou funkci, kterou aplikace volá. Vzhledem k tomu, že aplikace volají funkce knihovny DLL přes ukazatel, kompilátor negeneruje externí odkazy, takže není nutné propojení s knihovnou import. Je však nutné mít `typedef` příkaz nebo `using` , který definuje podpis volání exportovaných funkcí, které voláte.

- Při práci s knihovnou DLL volejte [FreeLibrary](freelibrary-and-afxfreelibrary.md) .

Například Tato ukázková funkce volá `LoadLibrary` načtení knihovny DLL s názvem "MyDll", volání `GetProcAddress` pro získání ukazatele na funkci s názvem "DLLFunc1", volá funkci a uloží výsledek a pak volání `FreeLibrary` k uvolnění knihovny DLL.

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

Na rozdíl od tohoto příkladu, ve většině případů byste měli volat `LoadLibrary` a `FreeLibrary` pouze jednou v aplikaci pro danou knihovnu DLL, zejména pokud budete volat více funkcí v knihovně DLL nebo opakované volání funkcí knihovny DLL.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Práce s knihovnami importu a soubory exportu](reference/working-with-import-libraries-and-export-files.md)

- [Pořadí hledání dynamických propojených knihoven](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Viz také:

[Vytváření C/C++ knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md)
