---
title: Chyba linkerů LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: b397ef8e551f8cd6179392541e35183a5850454f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357752"
---
# <a name="linker-tools-error-lnk1561"></a>Chyba linkerů LNK1561

vstupní bod musí být definován

Propojovací systém nenalezl *vstupní bod*, počáteční funkci pro volání ve spustitelném souboru. Ve `main` výchozím nastavení propojovací `wmain` program vyhledá nebo `WinMain` pro `wWinMain` mít funkci konzolové `DllMain` aplikace, nebo funkce aplikace pro Windows nebo dll, která vyžaduje inicializaci. Můžete zadat jinou funkci pomocí možnosti propojovacího systému [/ENTRY.](../../build/reference/entry-entry-point-symbol.md)

Tato chyba může mít několik příčin:

- Je možné, že jste nezahrnuli soubor, který definuje vstupní bod, do seznamu souborů, které chcete propojit. Ověřte, zda je soubor obsahující funkci vstupního bodu propojený s vaší aplikací.
- Je možné, že jste definovali vstupní bod pomocí nesprávného podpisu funkce; Například jste například chybně napsané nebo použité nesprávné případ pro název funkce nebo nesprávně zadali návratový typ nebo typy parametrů.
- Pravděpodobně jste nezadali možnost [/DLL](../../build/reference/dll-build-a-dll.md) při vytváření dll.
- Je možné, že jste při použití možnosti propojovacího zařízení [/ENTRY](../../build/reference/entry-entry-point-symbol.md) zadali název funkce vstupního bodu nesprávně.
- Pokud k vytvoření [dll.](../../build/reference/lib-reference.md) Pokud ano, odeberte soubor DEF ze sestavení.

Při vytváření aplikace propojovací program hledá funkci vstupního bodu pro volání pro spuštění kódu. Toto je funkce, která je volána po načtení aplikace a inicializována za běhu. Musíte zadat funkci vstupního bodu pro aplikaci, jinak se aplikace nedá spustit. Vstupní bod je pro dll volitelné. Ve výchozím nastavení propojovací zařízení hledá funkci vstupního bodu, která `int main(int, char**)`má jeden z několika konkrétních názvů a podpisů, například . Jako vstupní bod můžete zadat jiný název funkce pomocí možnosti propojovacího systému /ENTRY.

## <a name="example"></a>Příklad

Následující ukázka generuje LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
