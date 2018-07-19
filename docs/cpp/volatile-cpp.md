---
title: volatile (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- volatile_cpp
dev_langs:
- C++
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae3419cc7df0b9ed436981d5e845764a762c8ee8
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940964"
---
# <a name="volatile-c"></a>volatile (C++)
Kvalifikátor typu, který můžete použít k deklaraci, že hardware může objekt upraveno v programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
volatile declarator ;  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) přepínač kompilátoru upravit, jak kompilátor interpretuje toto klíčové slovo.  
  
 Visual Studio interpretuje **volatile** – klíčové slovo odlišně v závislosti na cílové architektuře. Pro ARM, pokud žádné **/volatile** – možnost kompilátoru je zadán, kompilátor provede jakoby **/volatile:iso** byly zadány. Pro architektury než ARM, pokud žádné **/volatile** – možnost kompilátoru je zadán, kompilátor provede jakoby **/volatile:ms** byly zadány; proto pro architektury jiné než jsme důrazně ARM doporučit, zadáte **/volatile:iso**a použijte explicitní synchronizací primitiv a vnitřních typů kompilátoru při jednání s pamětí, která je sdílena mezi vlákny.  
  
 Můžete použít **volatile** kvalifikátor pro poskytnutí přístupu k umístění v paměti, které jsou používány asynchronní procesy, jako jsou obslužné rutiny přerušení.  
  
 Když **volatile** se používá na proměnnou, která má také [kvalifikátor __restrict](../cpp/extension-restrict.md) – klíčové slovo, **volatile** má přednost před.  
  
 Pokud **struktura** člen je označen jako **volatile**, pak **volatile** rozšíří na celé struktury. Pokud struktura nemá žádné délkou, která je možné zkopírovat na aktuální architekturu pomocí jedné instrukce **volatile** může zcela ztraceno na danou strukturu.  
  
 **Volatile** – klíčové slovo může mít žádný vliv na pole, pokud je splněna jedna z následujících podmínek:  
  
-   Délka pole s modifikátorem volatile překračuje maximální velikost, je možné zkopírovat na aktuální architekturu pomocí jedné instrukce.  
  
-   Délka nejkrajnější obsahující **struktury**– nebo pokud je člen pravděpodobně vnořené **struktury**– překračuje maximální velikost, je možné zkopírovat na aktuální architekturu pomocí jedné instrukce.  
  
 I když procesor pořadí přístupu k paměti zrušení možné ukládat do mezipaměti, zrušení možné ukládat do mezipaměti proměnné musí být označen jako **volatile** zaručit, že kompilátor pořadí paměti používá.  
  
 Objekty, které jsou deklarovány jako **volatile** nepoužívají v některé optimalizace, protože jejich hodnoty můžete kdykoli změnit.  Systém vždy přečte aktuální hodnota objekt volatile na vyžádání, i v případě, že předchozí instrukce požádán o hodnotu ze stejného objektu.  Hodnota objektu se také zapíše okamžitě na přiřazení.  
  
## <a name="iso-compliant"></a>ISO předpisy  
 Pokud jste obeznámeni s C# klíčového slova volatile nebo zkušenosti s chováním **volatile** v dřívějších verzích Visual C++, mějte na paměti, která C ++ 11 standardu ISO **volatile** – klíčové slovo se liší a je podporováno v sadě Visual Studio při [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) je zadána možnost kompilátoru. (Pro ARM, je zadaný ve výchozím nastavení). **Volatile** – klíčové slovo v C ++ 11 ISO Standard kódu se dá použít jenom pro přístup k hardwaru; nepoužívejte ho pro komunikaci mezi vlákny. Pro komunikace mezi vlákny, použijte mechanismy pro zaslání [std::atomic\<T >](../standard-library/atomic.md) z [standardní knihovny C++](../standard-library/cpp-standard-library-reference.md).  
  
## <a name="end-of-iso-compliant"></a>Konec standardu ISO  
  
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Když **/volatile:ms** – možnost kompilátoru je používá – ve výchozím nastavení, když jsou cílové architektury než ARM – kompilátor vygeneruje další kód pro údržbu řazení mezi odkazy k nestálým objektům kromě zachování řazení s odkazy na jiné globální objekty. Zejména:  
  
-   Zápis do objektu volatile (označované také jako volatile zápisu) má sémantiku verze; To znamená odkaz na globální nebo statická objekt, který předchází zápis do objektu volatile postupně instrukce dojde před tohoto typu volatile zápisu v kompilované binární soubor.  
  
-   Sémantika získání; má čtení objektu volatile (označované také jako volatile pro čtení) To znamená, že odkaz na globální nebo statická objekt, ke které dojde po čtení paměti volatile postupně instrukce dojde po přečtení této volatile v kompilované binární soubor.  
  
 To umožňuje nestálým objektům použitého pro uzamčení paměti a verze ve vícevláknových aplikacích.  
  
> [!NOTE]
>  Když spoléhá na vylepšené záruka, že má zadaný při **/volatile:ms** – možnost kompilátoru je používá, kód není typu portable.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [klíčová slova](../cpp/keywords-cpp.md)   
 [Const](../cpp/const-cpp.md)   
 [Ukazatelé const a volatile](../cpp/const-and-volatile-pointers.md)