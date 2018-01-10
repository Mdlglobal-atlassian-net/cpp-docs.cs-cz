---
title: Popis argumentu | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3a9597ca8807c8ac1a3182b3daa1891a195c39c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="argument-description"></a>Popis argumentu
`argc` Parametr ve **hlavní** a **wmain** functions je celé číslo určující, kolik argumenty jsou předány program z příkazového řádku. Vzhledem k tomu, že název programu je považován za argument, hodnota `argc` alespoň jeden.  
  
## <a name="remarks"></a>Poznámky  
 `argv` Parametr je pole ukazatele na představující program argumenty řetězce ukončené hodnotou null. Každý element pole ukazuje na řetězcovou reprezentaci argument předaný **hlavní** (nebo **wmain**). (Informace o polích najdete v tématu [deklarace pole](../c-language/array-declarations.md).) `argv` Parametr lze deklarovat buď jako pole ukazatelé na typ `char` (`char *argv[]`) nebo jako ukazatel na ukazatele na typ `char` (`char **argv`). Pro **wmain**, `argv` parametr lze deklarovat buď jako pole ukazatelé na typ `wchar_t` (`wchar_t *argv[]`) nebo jako ukazatel na ukazatele na typ `wchar_t` (`wchar_t **argv`).  
  
 Podle konvence `argv` **[0]** je příkaz, ke které je voláno program.  Je však možné vytvořit, využívá proces [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425) a pokud používáte první a druhý argument (`lpApplicationName` a `lpCommandLine`), `argv` **[0]** nemusí být název spustitelného souboru; použít [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) načíst název spustitelného souboru.  
  
 Poslední ukazatele (`argv[argc]`) je **NULL**. (Viz [GETENV –](../c-runtime-library/reference/getenv-wgetenv.md) v *referenční dokumentace běhové knihovny* pro alternativní metoda pro získání informace o proměnných prostředí.)  
  
 **Konkrétní Microsoft**  
  
 `envp` Parametr je ukazatel na pole řetězce ukončené hodnotou null, které představují s hodnotami nastavenými v proměnných prostředí uživatele. `envp` Parametr lze deklarovat jako pole ukazatele na `char` (`char *envp[]`) nebo jako ukazatel na ukazatele na `char` (`char **envp`). V **wmain** funkce, `envp` parametr lze deklarovat jako pole ukazatele na `wchar_t` (`wchar_t *envp[]`) nebo jako ukazatel na ukazatele na `wchar_t` (`wchar_t **envp`). Je indikován konce pole **NULL** \*ukazatel. Všimněte si, že předaný bloku prostředí **hlavní** nebo **wmain** je "ukotvené" kopie aktuálního prostředí. Pokud později změníte prostředí prostřednictvím volání _**putenv –** nebo `_wputenv`, aktuální prostředí (jak ho vrátila `getenv` / `_wgetenv` a `_environ` nebo `_wenviron` proměnné) se změní, ale bloku na kterou odkazuje `envp` nedojde ke změně. `envp` Parametr je kompatibilní v C, ale ne v C++ ANSI.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)