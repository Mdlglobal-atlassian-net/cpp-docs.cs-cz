---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: 572fe244a076492e3f3316dd6d00f6fe7d7c3c9c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857200"
---
# <a name="volatile-c"></a>volatile (C++)

Kvalifikátor typu, který můžete použít k deklaraci, že objekt může být v programu upravený hardwarem.

## <a name="syntax"></a>Syntaxe

```
volatile declarator ;
```

## <a name="remarks"></a>Poznámky

Pomocí přepínače kompilátoru [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) můžete změnit způsob, jakým kompilátor interpretuje toto klíčové slovo.

Visual Studio interpretuje klíčové slovo **volatile** odlišně v závislosti na cílové architektuře. V případě ARM, pokud není zadána možnost kompilátoru **/volatile** , kompilátor provede jako if byl zadán parametr **/volatile: ISO** . Pro jiné architektury než ARM, pokud není zadána možnost kompilátoru **/volatile** , kompilátor provede, jako kdyby byl zadán parametr **/volatile: MS** . Proto pro jiné architektury než ARM důrazně doporučujeme, abyste zadali **/volatile: ISO**, a při práci s pamětí, která je sdílená napříč vlákny, používali explicitní a základní a vnitřní synchronizaci kompilátoru.

Můžete použít kvalifikátor **volatile** k poskytnutí přístupu k umístěním paměti, která jsou používána asynchronními procesy, jako jsou například obslužné rutiny přerušení.

Při použití **volatile** na proměnnou, která má také klíčové slovo [__restrict](../cpp/extension-restrict.md) , má **Nestálá** priorita.

Pokud je člen **struktury** označený jako **volatile**, pak se **volatile** rozšíří na celou strukturu. Pokud struktura nemá délku, kterou lze kopírovat na aktuální architekturu pomocí jedné instrukce, může být **volatile** zcela ztracena v této struktuře.

Klíčové slovo **volatile** nemusí mít žádný vliv na pole, pokud je splněna jedna z následujících podmínek:

- Délka pole volatile překračuje maximální velikost, která se dá zkopírovat na aktuální architekturu pomocí jedné instrukce.

- Délka vnější obsahující **struktury**– nebo pokud je členem možné vnořené **struktury**– překračuje maximální velikost, která se dá zkopírovat na aktuální architekturu pomocí jedné instrukce.

I když procesor nemění pořadí přístupu k paměti bez mezipaměti, proměnné bez mezipaměti musí být označeny jako **nestálé** , aby se zaručilo, že kompilátor nemění pořadí přístupů do paměti.

Objekty deklarované jako **volatile** se v některých optimalizacích nepoužívají, protože jejich hodnoty se můžou kdykoli změnit.  Systém při vyžádání vždy přečte aktuální hodnotu nestálého objektu, i když předchozí instrukce požádala o hodnotu ze stejného objektu.  Hodnota objektu je také zapsána ihned při přiřazení.

## <a name="iso-compliant"></a>Kompatibilní s ISO

Pokud jste obeznámeni s klíčovým C# slovem volatile nebo jste se seznámili s chováním **volatile** v C++ dřívějších verzích kompilátoru Microsoft (MSVC), je třeba si uvědomit, že **klíčové slovo Standard** ISO standard ISO se neshoduje a je podporováno v MSVC, pokud je zadána možnost kompilátoru [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) . (Pro ARM je standardně zadaný). Klíčové slovo **volatile** v kódu C++ 11 Standard ISO se používá pouze pro přístup k hardwaru. Nepoužívejte ho pro komunikaci mezi vlákny. Pro komunikaci mezi vlákny použijte mechanismy, jako je například [std:: Atomic\<t >](../standard-library/atomic.md) z [ C++ standardní knihovny](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Konec kompatibilního s ISO

**Specifické pro společnost Microsoft**

Při použití možnosti kompilátoru **/volatile: MS** – ve výchozím nastavení, pokud jsou architektury jiné než ARM zaměřené – kompilátor vygeneruje dodatečný kód pro zachování řazení mezi odkazy na nestálé objekty kromě udržování řazení odkazů na jiné globální objekty. Zejména:

- Zápis do nestálého objektu (označovaný také jako volatile zápisu) má sémantiku vydané verze; To znamená, že odkaz na globální nebo statický objekt, který se nachází před zápisem do objektu volatile v sekvenci instrukcí, bude proveden před stálým zápisem v kompilovaném binárním souboru.

- Čtení nestálého objektu (označované také jako nestálé čtení) má získat sémantiku. To znamená, že odkaz na globální nebo statický objekt, který se objeví po čtení těkavé paměti v sekvenci instrukcí, nastane po tomto nestálém binárním souboru.

To umožňuje, aby se nestálé objekty používaly pro zámky a uvolňování paměti ve vícevláknových aplikacích.

> [!NOTE]
>  Pokud spoléhá na zvýšenou záruku, která je k dispozici při použití možnosti kompilátoru **/volatile: MS** , kód není přenosný.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[Ukazatelé const a volatile](../cpp/const-and-volatile-pointers.md)