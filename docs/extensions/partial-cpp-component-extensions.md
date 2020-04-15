---
title: partial (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: 42e8cc9a20c96e65ed3ddf73d562fe014bd9fa28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349996"
---
# <a name="partial--ccli-and-ccx"></a>partial (C++/CLI a C++/CX)

**Částečné** klíčové slovo umožňuje různé části stejné třídy ref, které mají být vytvořeny nezávisle a v různých souborech.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Tato jazyková funkce se vztahuje pouze na prostředí Windows Runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

Pro ref třídy, která má dvě částečné definice, **částečné** klíčové slovo se použije na první výskyt definice a to se obvykle provádí automaticky generovaný kód, takže lidský kodér nepoužívá klíčové slovo velmi často. Pro všechny následné částečné definice třídy vynechte **částečný** modifikátor z klíčového slova *a* identifikátoru třídy. Když kompilátor narazí na dříve definovanou třídu ref a identifikátor třídy ref, ale žádné **částečné** klíčové slovo, interně kombinuje všechny části definice třídy ref do jedné definice.

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
Klíčové slovo, které deklaruje třídu nebo strukturu, která je podporována prostředím Windows Runtime. Buď **třída ref**, třída **value**, **struktura ref**, nebo **hodnota struct**.

*Identifikátor*<br/>
Název definovaného typu.

### <a name="remarks"></a>Poznámky

Částečná třída podporuje scénáře, kde upravíte jednu část definice třídy v jednom souboru a software pro automatické generování kódu – například návrhář xaml – upraví kód ve stejné třídě v jiném souboru. Pomocí částečné třídy můžete zabránit automatickému generátoru kódu v přepsání kódu. V projektu sady Visual Studio se **částečný** modifikátor automaticky použije na generovaný soubor.

Obsah: S dvěma výjimkami může definice částečné třídy obsahovat cokoli, co by definice celé třídy mohla obsahovat, pokud bylo vynecháno **částečné** klíčové slovo. Nelze však určit usnadnění přístupu třídy (například `public partial class X { ... };`) nebo **declspec**.

Specifikátory přístupu používané v definici částečné třídy pro *identifikátor* nemají vliv na výchozí usnadnění přístupu v následné částečné nebo úplné definici třídy pro *identifikátor*. Jsou povoleny včleněné definice statických datových členů.

Prohlášení: Částečná definice *identifikátoru* třídy zavádí pouze *identifikátor*názvu , ale *identifikátor* nelze použít způsobem, který vyžaduje definici třídy. *Identifikátor* názvu nelze použít k poznamování velikosti *identifikátoru*nebo k použití základního identifikátoru nebo člena *identifikátoru,* dokud kompilátor nenarazí na úplnou definici *identifikátoru*.

Číslo a řazení: Pro *identifikátor*může být nula nebo více částečných definic tříd . Každá částečná třída definice *identifikátoru* musí lexikálně předcházet jednu úplnou definici *identifikátoru* (pokud existuje úplná definice; jinak třídu nelze použít s výjimkou, jako by forward-declared), ale nemusí předcházet forwardprohlášení *identifikátoru*. Všechny třídy-klíče musí odpovídat.

Úplná definice: V bodě úplné definice *identifikátoru*třídy je chování stejné, jako kdyby definice *identifikátoru* deklarovala všechny základní třídy, členy atd.

Šablony: Částečná třída nemůže být šablonou.

Obecné typy: Částečná třída může být obecná, pokud úplná definice může být obecná. Ale každá částečná a úplná třída musí mít přesně stejné obecné parametry, včetně názvů formálních parametrů.

Další informace o použití **částečného** klíčového slova naleznete v [tématu Partial Classes (C++/CX).](https://go.microsoft.com/fwlink/p/?LinkId=249023)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

(Tato funkce jazyka se nevztahuje na soubor Common Language Runtime.)

## <a name="see-also"></a>Viz také

[Částečné třídy (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)
