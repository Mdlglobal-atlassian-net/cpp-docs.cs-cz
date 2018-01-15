---
title: "Mapování obecného textu v souboru Tchar.h | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: tchar.h
dev_langs: C++
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
caps.latest.revision: "12"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 405e95e9eb8fb760e2688e164178cf9270f31877
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="generic-text-mappings-in-tcharh"></a>Mapování obecného textu v souboru Tchar.h
Pro zjednodušení migrace kódu pro mezinárodní použití [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] poskytuje běhové knihovny [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]-konkrétní mapování obecného textu pro mnoho typů dat, rutiny a jiné objekty. Můžete použít tyto mapování, které jsou definovány v souboru Tchar.h zápis obecný kód, který může být sestaven pro jednobajtové, vícebajtové, nebo [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] znakových sad, v závislosti na manifestu konstanta, která je definována pomocí `#define` příkaz. Mapování obecného textu jsou [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] rozšíření, které nejsou [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)] kompatibilní.  
  
 Pomocí Tchar.h můžete vytvořit jednobajtové vícebajtových znakovou sadu (MBCS), a [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] aplikací ze stejného zdroje. Tchar.h definuje makra (která mají předponu `_tcs`), s správné definice preprocesoru, mapování na `str`, `_mbs`, nebo `wcs` podle potřeby. Pokud chcete vytvořit MBCS, definujte symbol `_MBCS`. K vytvoření [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)], definujte symbol `_UNICODE`. Chcete-li sestavit aplikaci jednobajtové, definovat ani (výchozí). Ve výchozím nastavení `_MBCS` je definována pro aplikace MFC.  
  
 `_TCHAR` Datový typ je definován v Tchar.h. Pokud je symbol `_UNICODE` je definována pro vaše sestavení `_TCHAR` je definován jako `wchar_t`, jinak hodnota jednobajtové a MBCS sestavení je definován jako `char`. (`wchar_t`, základní široká charakterová datového typu Unicode, je 16 bitů protějškem 8-bit podepsané `char`.) Mezinárodní aplikace, použijte `_tcs` řadu funkcí, které pracují v `_TCHAR` jednotky, ne v bajtech. Například `_tcsncpy` kopie `n` `_TCHARs`, nikoli `n` bajtů.  
  
 Protože některé jednoho bajtu znakových sad (SBCS) zpracování řetězců funkce proveďte (se znaménkem) `char*` parametry, výsledků upozornění kompilátoru Neshoda typu při `_MBCS` je definována. Existují tři způsoby, jak se vyhnout toto upozornění:  
  
1.  Převody funkce zajišťující bezpečnost typů vložených použijte v souboru Tchar.h. Toto je výchozí chování.  
  
2.  Použitím přímého makra v souboru Tchar.h definováním `_MB_MAP_DIRECT` na příkazovém řádku. Pokud to uděláte, musíte ručně spárovat typy. To je nejrychlejší způsob, ale není bezpečnost typů.  
  
3.  Převody funkce zajišťující bezpečnost typů staticky propojené knihovny použijte v souboru Tchar.h. Uděláte to tak, definujte konstantu `_NO_INLINING` na příkazovém řádku. Toto je metoda nejpomalejší, ale nejvíce bezpečnost typů.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Preprocesor – direktivy pro mapování obecného textu  
  
|definování #|Kompilované verze|Příklad|  
|---------------|----------------------|-------------|  
|`_UNICODE`|[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)](široké znaky)|`_tcsrev`se mapuje na`_wcsrev`|  
|`_MBCS`|Vícebajtových znaků|`_tcsrev`se mapuje na`_mbsrev`|  
|Žádný (výchozí hodnota je ani `_UNICODE` ani `_MBCS` definované)|SBCS ([!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)])|`_tcsrev`se mapuje na`strrev`|  
  
 Například funkce obecného textu `_tcsrev`, který je definován v souboru Tchar.h, se mapuje na `_mbsrev` Pokud jste definovali `_MBCS` v programu, nebo na `_wcsrev` Pokud jste definovali `_UNICODE`. V opačném `_tcsrev` mapuje `strrev`. Jiné mapování datového typu jsou uvedeny v Tchar.h pro programování jednoduchost, ale `_TCHAR` je velmi užitečné.  
  
### <a name="generic-text-data-type-mappings"></a>Mapování obecného textu datového typu  
  
|Obecného textu<br /><br /> Název datového typu|_UNICODE &<br /><br /> Není definována kódováním _MBCS|_MBCS<br /><br /> Definované|_UNICODE<br /><br /> Definované|  
|--------------------------------------|----------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`unsigned int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T`nebo`_TEXT`|Neplatí (odebraná pomocí preprocessor)|Neplatí (odebraná pomocí preprocessor)|`L`(převede následující znak nebo řetězec na jeho [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] protějšek)|  
  
 Seznam mapování obecného textu rutin, proměnné a další objekty, naleznete v části [mapování obecného textu](../c-runtime-library/generic-text-mappings.md) v referenci běhové knihovny.  
  
> [!NOTE]
>  Nepoužívejte `str` řadu funkcí s řetězci Unicode, které mohou obsahovat vložené null bajty. Podobně, nepoužívejte `wcs` rodiny funkcí s MBCS (nebo SBCS).  
  
 Následující fragmenty kódu ilustrují použití `_TCHAR` a `_tcsrev` pro mapování na MBCS, [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]a modely SBCS.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Pokud `_MBCS` byla definována, preprocesor namapuje tento fragment na tento kód:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Pokud `_UNICODE` byla definována, preprocesor namapuje tento fragment na tento kód:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Pokud ani `_MBCS` ani `_UNICODE` byly definovány, preprocesor namapuje fragment na jednobajtové [!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)] code, následujícím způsobem:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 Proto můžete napsat, udržovat a zkompilovat soubor jeden zdrojový kód pro spuštění rutiny, které jsou specifické pro všechny tři druhy znakových sad.  
  
## <a name="see-also"></a>Viz také  
 [Text a řetězce](../text/text-and-strings-in-visual-cpp.md)   
 [Použití datových typů TCHAR.H s kódováním _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)