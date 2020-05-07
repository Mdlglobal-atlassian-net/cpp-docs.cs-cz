---
title: Popis argumentu
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
ms.openlocfilehash: 88d477c874d62800c47bb03220246cb3f0999724
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492510"
---
# <a name="argument-description"></a>Popis argumentu

Parametr v **Main** a wmain funkce je celé číslo určující, kolik argumentů je předáno programu z příkazového řádku. **wmain** `argc` Vzhledem k tomu, že se název programu považuje za argument `argc` , hodnota je alespoň jedna.

## <a name="remarks"></a>Poznámky

`argv` Parametr je pole ukazatelů na řetězec zakončený hodnotou null reprezentující argumenty programu. Každý prvek pole odkazuje na řetězcové vyjádření argumentu předaného do **Main** (nebo **wmain**). (Informace o polích naleznete v tématu [deklarace polí](../c-language/array-declarations.md).) `argv` Parametr lze deklarovat buď jako pole ukazatelů na `char` typ (`char *argv[]`), nebo jako ukazatel na ukazatele na typ `char` (`char **argv`). Pro **wmain** `argv` lze parametr deklarovat buď jako pole ukazatelů na typ `wchar_t` (`wchar_t *argv[]`), nebo jako ukazatel na ukazatele na typ `wchar_t` (`wchar_t **argv`).

Podle konvence `argv`je **[0]** příkaz, se kterým je program vyvolán.  Je ale možné vytvořit proces pomocí funkce [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) a pokud použijete jak první, tak druhý argument (`lpApplicationName` a `lpCommandLine`), `argv` **[0]** nemusí být název spustitelného souboru; pomocí [GetModuleFileName –](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) načtěte název spustitelného souboru.

Poslední ukazatel (`argv[argc]`) má **hodnotu null**. (Další informace o tom, jak získat informace o proměnných prostředí, naleznete v tématu [getenv](../c-runtime-library/reference/getenv-wgetenv.md) v *Referenční příručce ke knihovně run-time* .)

**Specifické pro Microsoft**

`envp` Parametr je ukazatel na pole řetězců ukončených hodnotou null, které reprezentují hodnoty nastavené v proměnných prostředí uživatele. `envp` Parametr lze deklarovat jako pole ukazatelů `char` na (`char *envp[]`) nebo jako ukazatel na ukazatele na hodnotu `char` (`char **envp`). Ve funkci **wmain** může být `envp` parametr deklarován jako pole ukazatelů na `wchar_t` (`wchar_t *envp[]`) nebo jako ukazatel na ukazatele na hodnotu `wchar_t` (`wchar_t **envp`). Konec pole je označen ukazatelem s **hodnotou null** \*. Všimněte si, že blok prostředí předaný do **Main** nebo **wmain** je "zmrazená" kopie aktuálního prostředí. Pokud následně změníte prostředí prostřednictvím volání _**putenv** `_wputenv`nebo, dojde ke změně aktuálního prostředí (jak je `getenv` / `_wgetenv` vráceno a proměnných `_environ` nebo `_wenviron` ), ale blok, na `envp` který se odkazuje, se nezmění. `envp` Parametr je kompatibilní se standardem ANSI v jazyce C, ale ne v jazyce C++.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)
