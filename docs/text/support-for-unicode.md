---
title: Podpora pro Unicode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.assetid: 180f1d10-8543-4f79-85ce-293d3cb443bb
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: b58901f213d5e69eb50ad449a87266736fba0af7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="support-for-unicode"></a>Podpora pro Unicode
Unicode je specifikace pro podporu všech znakových sad, včetně těch, které nelze vyjádřit v právě jeden bajt. Pokud programujete pro mezinárodní trh, doporučujeme použít buď Unicode nebo [vícebajtové znakové sady](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS), nebo povolte vašeho programu, můžete ho vytvořit pro buď změnou přepínače.  
  
 Široká znaková je kód 2bajtová vícejazyčné znaků. Většina používaných v moderním počítačovém po celém světě, včetně technické symbolů a speciálních znaků pro publikování, můžete se znaky podle specifikace Unicode jako široký znak. Znaky, které nelze vyjádřit v právě jeden znak širokou představovat v páru Unicode pomocí funkce náhradní kódování Unicode. Protože každý široké znak je znázorněná s pevnou velikostí 16 bitů, pomocí široké znaky zjednodušuje programování s mezinárodními znakových sad.  
  
 Řetězec široká charakterová je reprezentován jako **[wchar_t]** pole a ukazuje `wchar_t*` ukazatel. Libovolný znak ASCII může být reprezentovaný jako široký znak prefixu písmena L znaku. L '\0' je například ukončení širokého (16 bitů) **NULL** znak. Podobně žádné ASCII řetězcový literál může být reprezentovaný jako široká charakterová řetězcový literál prefixu písmena L k literál ASCII (L "Hello").  
  
 Obecně platí široké znaky trvat další místo v paměti, než vícebajtové znaky, ale jsou rychlejší ke zpracování. Navíc jenom jeden národního prostředí může být reprezentován v daný okamžik v vícebajtové kódování, zatímco všechny znakové sady na světě jsou reprezentována současně reprezentace kódování Unicode.  
  
 Rozhraní MFC framework je kódování Unicode a MFC provede, povolení Unicode pomocí přenosných maker, jak je znázorněno v následující tabulce.  
  
### <a name="portable-data-types-in-mfc"></a>Přenosné datové typy v prostředí MFC  
  
|Bez přenositelností datový typ|Nahrazuje tento – makro|  
|-----------------------------|----------------------------|  
|`char`|_**TCHAR –**|  
|**Char\***, **LPSTR (Win32 datový typ)**|`LPTSTR`|  
|**const char\*, LPCSTR (Win32 datový typ)**|`LPCTSTR`|  
  
 Třída `CString` používá **_TCHAR** jako jeho základní a poskytuje konstruktory a operátory pro snadné převody. Většina řetězcových operací pro kódování Unicode lze zapsat pomocí stejné logiky, která používá pro zpracování znakovou sadu ANSI systému Windows, s tím rozdílem, že základní jednotkou operace je znak 16bitové místo 8bitové bajtů. Na rozdíl od práce vícebajtových znakových sad, můžete nemusíte (a neměli) zacházet se znaky Unicode, jako by šlo dva rozdílné bajty.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Instalace podpory znakové sady Unicode prostřednictvím knihovny MFC](../mfc/unicode-in-mfc.md)  
  
-   [Povolit kódování Unicode v mém programu](../text/international-enabling.md)  
  
-   [Povolit kódování Unicode a MBCS v mém programu](../text/internationalization-strategies.md)  
  
-   [Vytvoření mezinárodního programu pomocí kódování Unicode](../text/unicode-programming-summary.md)  
  
-   [Seznamte se s výhodami Unicode, včetně toho, jak pomocí znakové sady Unicode, umožňuje program efektivnější v systému Windows 2000](../text/benefits-of-character-set-portability.md)  
  
-   [Používat wmain, takže I široká charakterová argumenty předat programem](../text/support-for-using-wmain.md)  
  
-   [Zobrazit souhrn programování Unicode](../text/unicode-programming-summary.md)  
  
-   [Další informace o mapování obecného textu pro přenositelnost šířky bajtu](../text/generic-text-mappings-in-tchar-h.md)  
  
## <a name="see-also"></a>Viz také  
 [Text a řetězce](../text/text-and-strings-in-visual-cpp.md)   
 [Podpora použití funkce wmain](../text/support-for-using-wmain.md)