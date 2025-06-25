GCD: 

    def gcd(a, b):
        while b != 0:
            a, b = b, a % b
        return a
    
    print(gcd(66528, 52920))

ADVANCED GCD:


    def extended_gcd(a, b):
        if b == 0:
            return (a, 1, 0)  # gcd, u, v
        else:
            gcd, x1, y1 = extended_gcd(b, a % b)
            x = y1
            y = x1 - (a // b) * y1
            return (gcd, x, y)
    
    # Given
    p = 26513
    q = 32321
    
    gcd, u, v = extended_gcd(p, q)
    print("gcd:", gcd)
    print("u:", u)
    print("v:", v)
    print("flag:", min(u, v))

    
