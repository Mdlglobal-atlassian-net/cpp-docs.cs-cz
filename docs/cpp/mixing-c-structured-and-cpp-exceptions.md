---
title: Kombinace jazyka C (strukturované) a výjimky jazyka C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e632faddb3b4f59733710a915ed121a12f4e0c6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404860"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Kombinace výjimek v jazycích C (strukturované) a C++
Je-li zapotřebí vytvořit lépe přenositelný kód, není v programu jazyka C++ doporučeno používat zpracování strukturovaných výjimek. Však můžete někdy chtít kompilovat s **/EHa** spojit strukturované výjimky a zdrojový kód jazyka C++ a někdy třeba zařízení pro práci s oběma druhy výjimek. Protože obslužná rutina strukturované výjimky nemá žádný koncept objektů ani typových výjimek, nemůže zpracovat výjimky vyvolané z kódu jazyka C++ Nicméně C++ **catch** obslužné rutiny strukturované výjimky zpracovat mohou. Jako takové, syntaxe pro zpracování výjimek jazyka C++ (**zkuste**, **throw**, **catch**) neakceptuje kompilátor jazyka C, ale syntaxe zpracování strukturovaných výjimek (**__try** , **__except**, **__finally**) je podporována kompilátorem jazyka C++.  
  
 Zobrazit [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) informace o zpracování strukturovaných výjimek jako výjimek jazyka C++.  
  
 Jsou-li zkombinovány strukturované výjimky a výjimky jazyka C++, je třeba uvědomit si následující:  
  
1.  Výjimky jazyka C++ a strukturované výjimky nelze kombinovat v rámci stejné funkce.  
  
2.  Obslužné rutiny ukončení (**__finally** bloky) jsou provedeny vždy, i v případě odvíjení po vyvolání výjimky.  
  
3.  Zpracování výjimek jazyka C++ může zachytit a zachovat sémantiku odvíjení ve všech modulech zkompilovaných pomocí [/EH](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru (Tato možnost povoluje sémantiku odvíjení).  
  
4.  Mohou existovat situace, ve kterých nejsou funkce destruktoru volány pro všechny objekty. Například pokud se strukturovaná výjimka objeví při pokusu provést volání funkce prostřednictvím ukazatele neinicializované funkce, přičemž tato funkce přijímá jako parametry objekty, které byly vytvořeny před voláním, nebudou pro tyto objekty během odvíjení zásobníku volány destruktory.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?  
  
-   [Použití funkcí setjmp a longjmp v programech jazyka C++](../cpp/using-setjmp-longjmp.md)  
  
-   [Rozdíly mezi SEH a C++ EH](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>Viz také:  
 [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)