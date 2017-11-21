---
title: "&lt;FileSystem&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
dev_langs: C++
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b3587822536a6eff54b42c36b155836a9e49ab5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltfilesystemgt-operators"></a>&lt;FileSystem&gt; operátory
Operátory, proveďte lexikální porovnání dvě cesty řetězce. Použití **ekvivalentní** funkce k určení, zda dvě cesty (například relativní cesty a absolutní cesta) odkazovat na stejný soubor nebo adresář na disku.  
  
```  
C:\root> D:\root: false  
C:\root> C:\root\sub: false  
C:\root> C:\roo: true  
```  
  
 Další informace najdete v tématu [navigační systému souborů (C++)](../standard-library/file-system-navigation.md).  
  
## <a name="operator"></a>operator==  
  
```  
bool operator==(const path& left, const path& right) noexcept;  
```  
  
 Funkce vrátí hodnotu left.native() == right.native().  
  
## <a name="operator"></a>operator!=  
  
```  
bool operator!=(const path& left, const path& right) noexcept;  
```  
  
 Funkce vrátí hodnotu! (vlevo == vpravo).  
  
## <a name="operator"></a>operator<  
  
```  
bool operator<(const path& left, const path& right) noexcept;  
```  
  
 Funkce vrátí hodnotu left.native() < right.native().  
  
## <a name="operator"></a>operator<=  
  
```  
bool operator<=(const path& left, const path& right) noexcept;  
```  
  
 Funkce vrátí hodnotu! (vpravo \< levém).  
  
## <a name="operator"></a>operátor >  
  
```  
bool operator>(const path& left, const path& right) noexcept;  
```  
  
 Funkce vrátí hodnotu právo \< levé.  
  
## <a name="operator"></a>Operator > =  
  
```  
bool operator>=(const path& left, const path& right) noexcept;  
```  
  
 Funkce vrátí hodnotu! (levém < vpravo).  
  
## <a name="operator"></a>operátor nebo  
  
```  
path operator/(const path& left, const path& right);
```  
  
 Provede funkci:  
  
```  
basic_string<Elem, Traits> str;  
path ans = left;  
return (ans /= right);
```  
  
## <a name="operator"></a>operátor <<  
  
```  
template <class Elem, class Traits>  
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```  
  
 Funkce vrátí hodnotu os << pval.string\<Elem, vlastnosti > ().  
  
## <a name="operator"></a>operátor >>  
  
```  
template <class Elem, class Traits>  
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```  
  
 Provede funkci:  
  
```  
basic_string<Elem, Traits> str;  
is>> str;  
pval = str;  
return (is);
```  
  
## <a name="see-also"></a>Viz také  
 [Path – třída (standardní knihovna C++)](../standard-library/path-class.md)   
 [Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)   
 [\<FileSystem >](../standard-library/filesystem.md)

