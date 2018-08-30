---
title: Popis argumentu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cecc47bc4633aa40f38bda23d1aee0007ea34ab4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201879"
---
# <a name="argument-description"></a>Popis argumentu
`argc` Parametr **hlavní** a **wmain** funkce je celé číslo určující počet argumenty jsou předány do programu z příkazového řádku. Protože název programu je považován za argument hodnotu `argc` je alespoň jednou.  
  
## <a name="remarks"></a>Poznámky  
 `argv` Parametr je pole ukazatelů na řetězec zakončený null představující argumenty programu. Každý prvek pole odkazuje na řetězec představující argument předaný **hlavní** (nebo **wmain**). (Informace o polích naleznete v tématu [deklarace pole](../c-language/array-declarations.md).) `argv` Parametru lze deklarovat jako pole ukazatelů na typ `char` (`char *argv[]`) nebo jako ukazatel na ukazatele na typ `char` (`char **argv`). Pro **wmain**, `argv` parametru lze deklarovat jako pole ukazatelů na typ `wchar_t` (`wchar_t *argv[]`) nebo jako ukazatel na ukazatele na typ `wchar_t` (`wchar_t **argv`).  
  
 Podle konvence `argv` **[0]** příkaz, kterým je vyvolán program.  Nicméně je možné vytvořit podřízený proces pomocí [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) a pokud používáte první a druhý argument (`lpApplicationName` a `lpCommandLine`), `argv` **[0]** nemusí být název spustitelného souboru; použít [GetModuleFileName –](https://msdn.microsoft.com/library/windows/desktop/ms683197) k načtení názvu spustitelného souboru.  
  
 Poslední ukazatel (`argv[argc]`) je **NULL**. (Viz [getenv](../c-runtime-library/reference/getenv-wgetenv.md) v *Run-Time Library Reference* alternativní metody pro získání informací o proměnné prostředí.)  
  
 **Specifické pro Microsoft**  
  
 `envp` Parametru je ukazatel na pole řetězců zakončený hodnotou null, které představují hodnoty nastavené v proměnné prostředí uživatele. `envp` Parametru lze deklarovat jako pole ukazatelů na `char` (`char *envp[]`) nebo jako ukazatel na ukazatele na `char` (`char **envp`). V **wmain** funkce, `envp` parametru lze deklarovat jako pole ukazatelů na `wchar_t` (`wchar_t *envp[]`) nebo jako ukazatel na ukazatele na `wchar_t` (`wchar_t **envp`). Konec pole je označeno **NULL** \*ukazatele. Všimněte si, že blok prostředí předaný **hlavní** nebo **wmain** je "zmrazená" kopie aktuálního prostředí. Pokud později změníte prostředí prostřednictvím volání _**putenv** nebo `_wputenv`, aktuální prostředí (vrácené `getenv` / `_wgetenv` a `_environ` nebo `_wenviron` proměnné) se změní, ale blok odkazované `envp` nedojde ke změně. `envp` Parametr je ANSI kompatibilní v jazyce C, ale ne v jazyce C++.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)