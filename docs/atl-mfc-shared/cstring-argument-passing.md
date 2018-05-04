---
title: Předávání argumentů CString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 642ff20028a0929bb7bc11815e66b9f845ef9bd7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cstring-argument-passing"></a>Předávání argumentů CString
Tento článek vysvětluje, jak předat [CString](../atl-mfc-shared/reference/cstringt-class.md) objektů funkcí a jak vracet `CString` objekty z funkce.  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a> CString konvence předávání argumentů  
 Když definujete třídy rozhraní, musíte určit konvence předávání argumentů pro členské funkce. Existují některé standardní pravidla pro předávání a vrácení `CString` objekty. Pokud budete postupovat podle pravidel popsaných v [řetězce jako vstupy funkce](#_core_strings_as_function_inputs) a [řetězce jako funkce výstupy](#_core_strings_as_function_outputs), budete mít efektivní, správný kód.  
  
##  <a name="_core_strings_as_function_inputs"></a> Řetězce jako vstupy – funkce  
 Nejvíce efektivní a bezpečnou způsob, jak používat `CString` objekt ve volaných funkcí je předat `CString` objekt, který má funkci. Bez ohledu název `CString` objekt neukládá řetězec interně jako řetězec stylu jazyka C, která má hodnotu null. ukončovací znak. Místo toho `CString` objekt udržuje pečlivě sledovat počet znaků je. S `CString` poskytují `LPCTSTR` ukazatel na řetězce ukončené hodnotou null je malé množství práce, která se může stát důležité, aby to udělal neustále má váš kód. Výsledkem je dočasný, protože jakékoli změny `CString` obsah by způsobila neplatnost staré kopie `LPCTSTR` ukazatel.  
  
 V některých případech zadejte řetězec stylu jazyka C ho mít smysl. Například může být situaci, kdy volaná funkce je napsané v jazyce C a nepodporuje objekty. V takovém případě coerce `CString` parametru `LPCTSTR`, a funkce získají stylu jazyka C řetězce ukončené hodnotou null. Můžete také přejít opačným směrem a vytvořit `CString` objekt pomocí `CString` konstruktor, který přijímá řetězcový parametr stylu jazyka C.  
  
 Pokud řetězec obsah změnit, a funkce, deklarovat parametr jako nonconstant `CString` odkaz (**CString &**).  
  
##  <a name="_core_strings_as_function_outputs"></a> Řetězce jako výstupy – funkce  
 Obvykle se můžete vrátit `CString` objekty z funkcí, protože `CString` objekty podle hodnoty sémantiku jako primitivní typy. Chcete-li vrátit řetězec jen pro čtení, použijte konstanta `CString` odkaz (**const CString &**). Následující příklad ukazuje použití `CString` parametry a návratové typy:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)

