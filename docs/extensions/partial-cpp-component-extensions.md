---
title: částečné (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: f1837eb785f53e53a4b5ff621a898b0375cfc0fa
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786998"
---
# <a name="partial--ccli-and-ccx"></a>částečné (C + +/ CLI a C + +/ CX)

**Částečné** – klíčové slovo umožňuje různé části stejné třídy ref nebylo vytvořeno nezávisle a v různých souborech.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Tato funkce jazyka platí pouze pro prostředí Windows Runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

Pro ref class, která má dvě Částečná definice **částečné** – klíčové slovo se použije pro první výskyt definici, a to se obvykle provádí automaticky generovaný kód tak, aby lidské kodér není velmi často používat klíčové slovo. Všechny následné Částečná definice třídy, vynechejte **částečné** modifikátor *klíč třídy* – klíčové slovo a třída identifikátor. Když kompilátor narazí, dříve definovanou ref class a identifikátor třídy, ale ne **částečné** – klíčové slovo, interně kombinuje všechny části definice třídy ref do jednu definici.

### <a name="syntax"></a>Syntaxe

```cpp
partial class-key identifier {
   /* The first part of the partial class definition.
      This is typically auto-generated */
}
// ...
class-key identifier {
   /* The subsequent part(s) of the class definition. The same
      identifier is specified, but the "partial" keyword is omitted. */
}
```

### <a name="parameters"></a>Parametry

*class-key*<br/>
Klíčové slovo, který deklaruje třídy nebo struktury, která je podporována modulem Windows Runtime. Buď **třídy ref class**, **hodnotu třídy**, **ref struct**, nebo **hodnotu struktury**.

*identifier*<br/>
Název definovaný typ.

### <a name="remarks"></a>Poznámky

Částečné třídy podporuje scénáře, kde můžete upravit jednu část definice třídy v jednom souboru a automatické generování kódu softwaru – například Návrhář XAML – upravuje kód ve stejné třídě v jiném souboru. S použitím částečnou třídu, můžete zabránit generátor kódu automatické přepsání kódu. V projektu sady Visual Studio **částečné** modifikátor se použijí automaticky generovaného souboru.

Obsah: Se dvěma výjimkami, definicí částečné třídy může obsahovat cokoli, co by mohly obsahovat definici úplné třídy, pokud **částečné** – klíčové slovo byl vynechán. Však nelze zadat třídu přístupnosti (například `public partial class X { ... };`), nebo **declspec**.

Přístup k specifikátorů použitých v definici částečné třídy pro *identifikátor* nemají vliv na výchozí dostupnost v definici třídy následné částečné nebo úplné *identifikátor*. Vložená definice členů statických dat jsou povoleny.

Deklarace: Částečnou definici třídy *identifikátor* pouze zavádí název *identifikátor*, ale *identifikátor* nelze použít tak, aby vyžaduje definici třídy. Název *identifikátor* nelze zjistit velikost *identifikátor*, nebo použít základní nebo členský z *identifikátor* až poté, co kompilátor narazí kompletní definici *identifikátor*.

Počet a pořadí: Může být nula nebo více definicí částečné třídy pro *identifikátor*. Každá definice částečné třídy *identifikátor* musí předcházet lexikálně jeden kompletní definici *identifikátor* (Pokud je úplná definice; v opačném případě třídu nelze použít s výjimkou jako dopředně deklarované), ale nemusí předcházet dopředné deklarace *identifikátor*. Všechny klíče třídy se musí shodovat.

Úplná definice: Přejme během úplné definice třídy *identifikátor*, chování je stejné jako definice *identifikátor* měl deklarovat základních tříd, členů, atd., v pořadí, ve kterém se nacházely došlo k a definované v částečné třídy.

Šablony: Částečná třída nemůže být šablona.

Obecné typy: Částečné třídy může být obecný, pokud je úplná definice může být obecný. Ale každý úplné a částečné třídy musí mít přesně stejné obecné parametry, včetně názvy formálních parametrů.

Další informace o tom, jak používat **částečné** – klíčové slovo, naleznete v tématu [částečné třídy (C + +/ CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

(Této funkci jazyka neplatí pro modul Common Language Runtime.)

## <a name="see-also"></a>Viz také

[Částečné třídy (C + +/ CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)