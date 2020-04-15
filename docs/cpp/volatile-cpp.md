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
ms.openlocfilehash: 841b2e1e4ffbec87a170c45be8ad0cd0f831a0ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371902"
---
# <a name="volatile-c"></a>volatile (C++)

Kvalifikátor typu, který můžete použít k deklarování, že objekt může být v programu změněn hardwarem.

## <a name="syntax"></a>Syntaxe

```
volatile declarator ;
```

## <a name="remarks"></a>Poznámky

Přepínač kompilátoru [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) můžete použít k úpravě způsobu interpretace tohoto klíčového slova kompilátoru.

Visual Studio interpretuje **těkavé** klíčové slovo odlišně v závislosti na cílové architektury. Pro ARM, pokud není zadána žádná možnost **/volatile** kompilátoru, kompilátor provádí, jako kdyby **/volatile:iso** byly zadány. Pro architektury než ARM, pokud není zadána žádná možnost **/volatile** kompilátoru, kompilátor provádí, jako by **/volatile:ms byly zadány;** proto pro architektury než ARM důrazně doporučujeme zadat **/volatile:iso**a použít explicitní synchronizace primitiv a vlastní objekty kompilátoru, pokud máte co do činění s pamětí, která je sdílena v rámci vláken.

**Volatile** kvalifikátor můžete použít k poskytnutí přístupu k umístění paměti, které jsou používány asynchronní procesy, jako jsou obslužné rutiny přerušení.

Při **volatile** se používá na proměnnou, která má také klíčové slovo [__restrict,](../cpp/extension-restrict.md) **volatile** má přednost.

Pokud **je člen struktury** označen jako **těkavý**, je **těkavá** šířena do celé struktury. Pokud struktura nemá délku, kterou lze zkopírovat na aktuální architektuře pomocí jedné instrukce, může být **volatile** zcela ztracena na této struktuře.

**Volatilní** klíčové slovo může mít žádný vliv na pole, pokud je splněna jedna z následujících podmínek:

- Délka těkavého pole překračuje maximální velikost, kterou lze zkopírovat na aktuální architektuře pomocí jedné instrukce.

- Délka nejkrajnější obsahující **struktury**– nebo pokud je členem případně vnořené **struktury**– překračuje maximální velikost, kterou lze zkopírovat na aktuální architektuře pomocí jedné instrukce.

Přestože procesor nepřizpůsobuje pořadí přístupů do paměti, kterou nelze uložit do mezipaměti, musí být proměnné, které nelze uložit do mezipaměti, označeny jako **nestálé,** aby bylo zaručeno, že kompilátor nezmění pořadí přístupů do paměti.

Objekty, které jsou deklarovány jako **nestálé,** se v určitých optimalizacích nepoužívají, protože jejich hodnoty se mohou kdykoli změnit.  Systém vždy čte aktuální hodnotu těkavého objektu, pokud je požadováno, i v případě, že předchozí instrukce požádal o hodnotu ze stejného objektu.  Hodnota objektu je také zapsána okamžitě na přiřazení.

## <a name="iso-compliant"></a>Kompatibilní s ISO

Pokud jste obeznámeni s c# volatile klíčové slovo nebo obeznámeni s **chováním volatile** v dřívějších verzích kompilátoru Microsoft C++ (MSVC), uvědomte si, že C ++ 11 ISO Standard **volatile** klíčové slovo se liší a je podporován v MSVC při [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) kompilátor možnost je zadán. (Pro ARM je zadán ve výchozím nastavení). **Těkavé** klíčové slovo v kódu Standard standardu Jazyka C++11 má být použito pouze pro přístup k hardwaru. nepoužívejte jej pro komunikaci mezi vlákny. Pro komunikaci mezi vlákny použijte mechanismy, jako je [std::atomic\<T>](../standard-library/atomic.md) ze standardní [knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Konec kompatibilního s ISO

**Specifické pro Microsoft**

Při **/volatile:ms** kompilátor možnost – ve výchozím nastavení při architektury než ARM jsou cílené – kompilátor generuje další kód pro udržení řazení mezi odkazy na nestálé objekty kromě udržování řazení na odkazy na jiné globální objekty. Zejména jde o toto:

- Zápis do těkavého objektu (označovaný také jako volatile write) má sémantiku Release; to znamená, že odkaz na globální nebo statický objekt, ke kterému dochází před zápisem do těkavého objektu v posloupnosti instrukcí dojde před tímto volatilním zápisem v kompilovaném binárním souboru.

- Čtení těkavého objektu (označované také jako nestálé čtení) má sémantiku Získat; to znamená, že odkaz na globální nebo statický objekt, ke kterému dojde po čtení nestálé paměti v posloupnosti instrukcí dojde po tomto nestálém čtení v kompilovaném binárním souboru.

To umožňuje nestálé objekty, které mají být použity pro uzamčení paměti a uvolnění v aplikacích s více vlákny.

> [!NOTE]
> Když se spoléhá na rozšířené záruky, která je k dispozici při **/volatile:ms** kompilátor možnost je použita, kód je nepřenosný.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[Ukazatelé const a volatile](../cpp/const-and-volatile-pointers.md)
