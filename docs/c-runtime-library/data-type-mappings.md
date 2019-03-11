---
title: Mapování datového typu
ms.date: 11/04/2016
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
ms.openlocfilehash: 60dc4329ae4c908b9bd168584c71c42c12634bb2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749097"
---
# <a name="data-type-mappings"></a>Mapování datového typu

Tato mapování datového typu jsou definovány v TCHAR. H a závisí na tom, zda konstanty `_UNICODE` nebo `_MBCS` je definována v programu.

Související informace naleznete v tématu [pomocí TCHAR. H datové typy s kódováním _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md).

### <a name="generic-text-data-type-mappings"></a>Mapování obecného textu datových typů

|Obecného textu<br /><br /> Název datového typu|SBCS (_UNICODE,<br /><br /> _MBCS nejsou<br /><br /> definice)|_MBCS<br /><br /> definováno|_UNICODE<br /><br /> definováno|
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|
|`_TCHAR`|`char`|`char`|`wchar_t`|
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|
|`_TINT`|`int`|`int`|`wint_t`|
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|
|`_T` Nebo `_TEXT`|Žádný vliv (odebral preprocesoru)|Žádný vliv (odebral preprocesoru)|`L` (převede následující znak nebo řetězec k jeho protějšku Unicode)|

## <a name="see-also"></a>Viz také:

[Mapování obecného textu](../c-runtime-library/generic-text-mappings.md)<br/>
[Mapování konstant a globálních proměnných](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Mapování rutin](../c-runtime-library/routine-mappings.md)<br/>
[Ukázka programu obecného textu](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Použití mapování obecného textu](../c-runtime-library/using-generic-text-mappings.md)
