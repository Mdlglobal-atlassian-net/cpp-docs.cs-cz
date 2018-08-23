---
title: Mapování obecného textu v souboru Tchar.h | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9769e1af4f9a1aa8c2c347d8724712b52e03bc22
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606486"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mapování obecného textu v souboru Tchar.h
Pro zjednodušení, přenos kódu pro mezinárodní použití, běhové knihovny Microsoft poskytuje mapování obecného textu specifické pro společnost Microsoft pro mnoho typů dat, rutiny a dalších objektů. Můžete použít tato mapování, které jsou definovány v souboru Tchar.h se zapsat obecný kód, který může být sestaven pro jednobajtové, vícebajtové, nebo nastaví znak Unicode, v závislosti na konstanta manifestu, který definujete pomocí `#define` příkazu. Mapování obecného textu jsou rozšíření společnosti Microsoft, které nejsou kompatibilní ANSI.  
  
 Pomocí Tchar.h, můžete vytvořit jednobajtové vícebajtové znakové sady (MBCS) a Unicode aplikace ze stejného zdroje. Definuje Tchar.h makra (která mají předponu `_tcs`) s správné definice preprocesoru, které mapují na `str`, `_mbs`, nebo `wcs` funkcí, podle potřeby. Pokud chcete vytvořit znakové sady MBCS, definujte symbol `_MBCS`. Chcete-li sestavit Unicode, definujte symbol `_UNICODE`. Chcete-li sestavit aplikaci jednobajtové, definovat ani (výchozí). Ve výchozím nastavení `_MBCS` je definováno pro aplikace knihovny MFC.  
  
 `_TCHAR` Datový typ je definován v souboru Tchar.h. Pokud se symbol `_UNICODE` je definována pro sestavení, `_TCHAR` je definován jako **wchar_t**; v opačném případě jednobajtové a znakové sady MBCS sestavení, je definován jako **char**. (**wchar_t**, je základní typ dat širokého znaku Unicode protějškem 16 bitů 8 bitů podepsané **char**.) Mezinárodní aplikace, použijte `_tcs` řadu funkcí, které fungují v `_TCHAR` jednotky, ne v bajtech. Například `_tcsncpy` kopie `n` `_TCHARs`, nikoli `n` bajtů.  
  
 Protože některé řetězce zpracování jeden bajt znakových sad (SBCS) funkce vzít (se znaménkem) `char*` parametry, výsledků upozornění kompilátoru Neshoda typů při `_MBCS` je definována. Chcete tomuto upozornění předejít třemi způsoby:  
  
1.  V souboru Tchar.h pomocí převodní rutiny zajišťující bezpečnost typů vložené funkce. Toto je výchozí chování.  
  
2.  Použijte přímý makra v souboru Tchar.h definováním `_MB_MAP_DIRECT` na příkazovém řádku. Pokud to uděláte, musíte ručně odpovídají typům. Toto je nejrychlejší způsob, ale není typově bezpečný.  
  
3.  V souboru Tchar.h pomocí převodní rutiny funkce staticky propojené knihovny typově bezpečné. Uděláte to tak, definujte konstantu `_NO_INLINING` na příkazovém řádku. Toto je metoda nejpomalejší ale nejvíce typově bezpečné.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Direktivy preprocesoru pro mapování obecného textu  
  
|definování #|Kompilovaná verze|Příklad|  
|---------------|----------------------|-------------|  
|`_UNICODE`|Kódování Unicode (širokého znaku)|`_tcsrev` Mapuje se na `_wcsrev`|  
|`_MBCS`|Vícebajtových znaků|`_tcsrev` Mapuje se na `_mbsrev`|  
|None (výchozí nastavení nemá žádný `_UNICODE` ani `_MBCS` definované)|SBCS (ASCII)|`_tcsrev` Mapuje se na `strrev`|  
  
 Například obecná textová funkce `_tcsrev`, která je definovaná v souboru Tchar.h se mapuje na `_mbsrev` Pokud jste definovali `_MBCS` v aplikaci nebo na `_wcsrev` Pokud jste definovali `_UNICODE`. V opačném případě `_tcsrev` mapuje `strrev`. Mapování jiných datových typů jsou k dispozici v souboru Tchar.h ke zvýšení pohodlí programování, ale `_TCHAR` je nejužitečnější.  
  
### <a name="generic-text-data-type-mappings"></a>Mapování obecného textu datových typů  
  
|Obecného textu<br /><br /> Název datového typu|_UNICODE &AMP;<br /><br /> _MBCS nejsou definovány|_MBCS<br /><br /> Definice|_UNICODE<br /><br /> Definice|  
|--------------------------------------|----------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|**char**|**char**|**wchar_t**|  
|`_TINT`|**int**|**unsigned int**|`wint_t`|  
|`_TSCHAR`|**podepsané char**|**podepsané char**|**wchar_t**|  
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|  
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|  
|`_T` Nebo `_TEXT`|Žádný vliv (odebral preprocesoru)|Žádný vliv (odebral preprocesoru)|`L` (převede následující znak nebo řetězec k jeho protějšku Unicode)|  
  
 Seznam mapování obecného textu rutiny, proměnných a dalších objektů najdete v tématu [mapování obecného textu](../c-runtime-library/generic-text-mappings.md) v referenční dokumentace knihoven Run-Time.  
  
> [!NOTE]
>  Nepoužívejte `str` řady funkcí s řetězců v kódu Unicode, které by mohly obsahovat vložený bajty s hodnotou null. Podobně, nepoužívejte `wcs` řady funkcí s znakové sady MBCS (nebo SBCS).  
  
 Následující fragmenty kódu ukazují použití `_TCHAR` a `_tcsrev` mapování znakové sady MBCS, Unicode a knihovna SBCS modely.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Pokud `_MBCS` byl definován, preprocesor mapuje na tento kód tento fragment:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Pokud `_UNICODE` byl definován, preprocesor mapuje na tento kód tento fragment:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Pokud ani `_MBCS` ani `_UNICODE` byly definovány, preprocesor mapuje fragment kódu ASCII jednobajtové, následujícím způsobem:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 Proto můžete psát, udržovat a zkompilujte soubor jeden zdrojový kód pro spuštění rutiny, které jsou specifické pro všechny tři druhy znakových sad.  
  
## <a name="see-also"></a>Viz také  
 [Text a řetězce](../text/text-and-strings-in-visual-cpp.md)   
 [Použití datových typů TCHAR.H s kódováním _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)