---
title: Chyba linkerů LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: 706cf6c90dc187b6c343edc82cebb93bb8660452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194847"
---
# <a name="linker-tools-error-lnk1561"></a>Chyba linkerů LNK1561

vstupní bod musí být definovaný.

Linker nenalezl *vstupní bod*, počáteční funkci pro volání ve spustitelném souboru. Ve výchozím nastavení linker hledá `main` nebo `wmain` funkce pro konzolovou aplikaci, `WinMain` nebo `wWinMain` funkce pro aplikaci pro Windows, nebo `DllMain` pro knihovnu DLL, která vyžaduje inicializaci. Jinou funkci můžete zadat pomocí možnosti linkeru [/entry](../../build/reference/entry-entry-point-symbol.md) .

Tato chyba může mít několik příčin:
- Možná jste nezahrnuli soubor definující vstupní bod v seznamu souborů k propojení. Ověřte, zda je soubor, který obsahuje funkci vstupního bodu, propojen do vaší aplikace.
- Je možné, že jste vstupní bod definovali pomocí špatné signatury funkce. Například je možné, že jste nesprávně nastavili nebo nepoužili špatný případ pro název funkce, nebo pokud jste nezadali typ návratového typu nebo parametru.
- Možná jste nezadali možnost [/DLL](../../build/reference/dll-build-a-dll.md) při vytváření knihovny DLL.
- Pokud jste použili možnost linkeru [/entry](../../build/reference/entry-entry-point-symbol.md) , je možné, že jste nesprávně zadali název funkce vstupního bodu.
- Používáte-li nástroj [lib](../../build/reference/lib-reference.md) k sestavení knihovny DLL, je možné, že jste zadali soubor. def. Pokud ano, odeberte soubor. def ze sestavení.

Při sestavování aplikace linker hledá funkci vstupního bodu pro volání ke spuštění kódu. Toto je funkce, která je volána po načtení aplikace a inicializaci modulu runtime. Pro aplikaci musíte zadat funkci vstupního bodu, jinak se aplikace nedá spustit. Vstupní bod je volitelný pro knihovnu DLL. Ve výchozím nastavení linker hledá funkci vstupního bodu, která má jeden z několika specifických názvů a podpisů, například `int main(int, char**)`. Další název funkce můžete zadat jako vstupní bod pomocí možnosti linkeru/ENTRY.

## <a name="example"></a>Příklad

Následující ukázka generuje LINKERŮ LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
