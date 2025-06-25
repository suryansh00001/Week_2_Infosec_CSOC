MODULAR EXPLOITAATION:

    flag = pow(10, 17, 22663)
    print(flag)

PUBLIC KEYS:

    ct = pow(12, 65537, 391)
    print(ct)

EULER TOTIENT:

    p = 857504083339712752489993810777
    q = 1029224947942998075080348647219
    
    phi_n = (p - 1) * (q - 1)
    print(phi_n)

PRIVATE KEYS:

    from Crypto.Util.number import inverse

    p = 857504083339712752489993810777
    q = 1029224947942998075080348647219
    e = 65537
    
    phi = (p - 1) * (q - 1)
    d = inverse(e, phi)
    print(d)


RSA DECRYPTION:


    from Crypto.Util.number import long_to_bytes
    
    N = 882564595536224140639625987659416029426239230804614613279163
    d = 121832886702415731577073962957377780195510499965398469843281
    c = 77578995801157823671636298847186723593814843845525223303932
    
    pt = pow(c, d, N)
    flag = long_to_bytes(pt)
    print(flag)

PUBLIC EXPONENTS: SALTY


    from Crypto.Util.number import long_to_bytes
    
    ct = 44981230718212183604274785925793145442655465025264554046028251311164494127485
    flag = long_to_bytes(ct)
    print(flag)





