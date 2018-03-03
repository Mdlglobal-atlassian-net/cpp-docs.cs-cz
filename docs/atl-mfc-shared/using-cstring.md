---
title: "Pomocí CString | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3844e10dc12207513e074e76e822e4999fadec7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-cstring"></a>Pomocí CString
Témata v této části popisují, jak programovat s `CString`. Pro referenční dokumentaci o `CString` třídy, najdete v dokumentaci k [CStringT](../atl-mfc-shared/reference/cstringt-class.md).  
  
 Chcete-li použít `CString`, zahrnout `atlstr.h` záhlaví.  
  
 `CString`, `CStringA`, A `CStringW` třídy jsou specializací šabloně třída s názvem [CStringT](../atl-mfc-shared/reference/cstringt-class.md) na základě typu dat znak podporují.  
  
 A `CStringW` objekt obsahuje `wchar_t` zadejte a podporuje řetězců v kódu Unicode. A `CStringA` objekt obsahuje `char` typu a řetězce podporuje jednobajtové a vícebajtové (znakové sady MBCS). A `CString` objekt podporuje buď `char` typu nebo `wchar_t` typu, v závislosti na tom, jestli `MBCS` symbol nebo `UNICODE` symbol je definována v době kompilace.  
  
 A `CString` objekt uchová textová data `CStringData` objektu. `CString`přijímá `null`-ukončenou stylu jazyka C řetězce, ale není zachována `null` znak v datech uložených znak. Místo toho `CString` sleduje řetězec délky. `CString`poskytnout zakončením hodnotu null, když exportuje řetězec stylu jazyka C. Můžete vložit `null` v `CString`, ale jeho může vést k neočekávaným výsledkům.  
  
 Následující sadu řetězec třídy lze použít bez propojení knihovny MFC, s nebo bez CRT – podpora: `CAtlString`, `CAtlStringA`, a `CAtlStringW`.  
  
 `CString`se používá v nativní projekty. Pro spravovaný kód (C + +/ CLI) projektů, použití `System::String`.  
  
 Chcete-li přidat další možnosti než `CString`, `CStringA`, nebo `CStringW` nyní nenabízejí, měli byste vytvořit podtřídou třídy `CStringT` obsahující další funkce.  
  
 Následující kód ukazuje, jak vytvořit `CString` a tisku na standardní výstup:  
  
```cpp  
#include <atlstr.h>  
  
int main() {  
    CString aCString = CString(_T("A string"));  
    _tprintf(_T("%s"), (LPCTSTR) aCString);  
}  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CString – základní operace](../atl-mfc-shared/basic-cstring-operations.md)  
 Popisuje základní `CString` operace, včetně vytváření objektů z C řetězcové literály, přístup k jednotlivých znaků `CString`, zřetězení dva objekty a porovnávání `CString` objekty.  
  
 [Správa řetězcových dat](../atl-mfc-shared/string-data-management.md)  
 Popisuje použití kódování Unicode a MBCS s `CString`.  
  
 [CString – sémantika](../atl-mfc-shared/cstring-semantics.md)  
 Vysvětluje, jak `CString` objekty se používají.  
  
 [CString – operace týkající se řetězců ve stylu jazyka C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)  
 Popisuje manipulace s obsah `CString` objekt jako řetězec stylu jazyka C ukončené hodnotou null.  
  
 [Přidělování a uvolňování pro BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)  
 Popisuje použití paměti pro `BSTR` a objekty modelu COM.  
  
 [CString – čištění výjimek](../atl-mfc-shared/cstring-exception-cleanup.md)  
 Vysvětluje, že explicitní vyčištění v MFC 3.0 a novější už není nezbytné.  
  
 [CString – předávání argumentů](../atl-mfc-shared/cstring-argument-passing.md)  
 Vysvětluje, jak předat CString – objekty funkcí a jak vracet `CString` objekty z funkce.  
  
 [Podpora znakových sad Unicode a MBCS](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)  
 Popisuje, jak MFC je povolený pro kódování Unicode a MBCS podporovat.  
  
## <a name="reference"></a>Odkaz  
 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)  
 Poskytuje referenční informace o `CStringT` třídy.  
  
 [CSimpleStringT – třída](../atl-mfc-shared/reference/csimplestringt-class.md)  
 Poskytuje referenční informace o `CSimpleStringT` třídy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
 Obsahuje odkazy na témata, která popisují několik způsobů, jak spravovat data řetězec.  
  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)

