---
title: částečný (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: ad8faa08a2c85e777cbc8721e5842e708b9e6cb1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181847"
---
# <a name="partial--ccli-and-ccx"></a>částečný (C++/CLI a C++/CX)

Klíčové slovo **Partial** umožňuje vytvářet různé části stejné referenční třídy nezávisle na sobě a v různých souborech.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Tato funkce jazyka se vztahuje pouze na prostředí Windows Runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

Pro referenční třídu, která má dvě částečné definice, je klíčové slovo **Partial** použito pro první výskyt definice a to je obvykle prováděno automaticky generovaným kódem, aby lidský programátor nepoužíval klíčové slovo velmi často. Pro všechny následné částečné definice třídy vynechejte **částečný** modifikátor z klíčového slova *Class-Key* a identifikátor třídy. Když kompilátor narazí na dříve definovanou referenční třídu a identifikátor třídy, ale žádné **částečné** klíčové slovo, interně kombinuje všechny části definice referenční třídy do jedné definice.

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

*klíč třídy*<br/>
Klíčové slovo, které deklaruje třídu nebo strukturu, kterou prostředí Windows Runtime podporuje. Buď **ref class**, **Value Class**, **ref struct**nebo **value struct**.

*RID*<br/>
Název definovaného typu.

### <a name="remarks"></a>Poznámky

Částečná třída podporuje scénáře, kdy upravíte jednu část definice třídy v jednom souboru a automatický software pro generování kódu – například Návrhář XAML – upraví kód ve stejné třídě v jiném souboru. Pomocí částečné třídy můžete zabránit automatickému generátoru kódu v přepsání kódu. V projektu sady Visual Studio je **částečný** modifikátor použit automaticky pro vygenerovaný soubor.

Obsah: se dvěma výjimkami může definice částečné třídy obsahovat cokoli, co definice celé třídy může obsahovat, pokud bylo vynecháno **částečné** klíčové slovo. Nemůžete však zadat přístupnost třídy (například `public partial class X { ... };`) nebo **declspec**.

Specifikátory přístupu použité v definici částečné třídy pro *identifikátor* nemají vliv na výchozí přístupnost v následné částečné nebo úplné definici třídy pro *identifikátor*. Vložené definice statických datových členů jsou povoleny.

Deklarace: Částečná definice *identifikátoru* třídy zavádí jenom *identifikátor*názvu, ale *identifikátor* se nedá použít způsobem, který vyžaduje definici třídy. *Identifikátor* názvu se nedá použít k zjištění velikosti *identifikátoru*nebo k použití základního nebo členu *identifikátoru* , dokud kompilátor nenalezne úplnou definici *identifikátoru*.

Počet a řazení: pro *identifikátor*může být k dispozici nula nebo více definic dílčí třídy. Každá definice dílčí třídy *identifikátoru* musí být lexikální před jednou úplnou definicí *identifikátoru* (pokud existuje úplná definice), jinak třída nemůže být použita s výjimkou toho, pokud je deklarováno předem, ale nemusí předcházet deklaraci deklarací *identifikátoru*. Všechny klíče třídy se musí shodovat.

Úplná definice: v bodě úplné definice *identifikátoru*třídy je chování stejné, jako by definice *identifikátoru* měla deklarovat všechny základní třídy, členy atd. v pořadí, ve kterém byly nalezeny a definovány v dílčích třídách.

Šablony: částečná třída nemůže být šablonou.

Obecné typy: částečná třída může být obecná, pokud by byla úplná definice Obecná. Každá částečná a plná třída ale musí mít přesně stejné obecné parametry, včetně formálních názvů parametrů.

Další informace o použití klíčového slova **Partial** naleznete v tématu [Partial Classes (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

(Tato funkce jazyka se nevztahuje na modul CLR (Common Language Runtime).)

## <a name="see-also"></a>Viz také

[Částečné třídy (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)
