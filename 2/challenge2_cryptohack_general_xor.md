1) BASIC XOR

         label = "label"
        result = ""
        
        for c in label:
            xor_char = chr(ord(c) ^ 13)
            result += xor_char
        
        print("Result:", result)

   output: aloha


2)XOR IS COMMUTATIVE


    from binascii import unhexlify
    
    def xor(a, b):
        return bytes(x ^ y for x, y in zip(a, b))
    
    # Step 1: Parse all hex
    KEY1 = bytes.fromhex("a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313")
    KEY2_xor_KEY1 = bytes.fromhex("37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e")
    KEY2_xor_KEY3 = bytes.fromhex("c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1")
    FLAG_xor_all = bytes.fromhex("04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf")
    
    # Step 2: Recover KEY2
    KEY2 = xor(KEY1, KEY2_xor_KEY1)
    
    # Step 3: Recover KEY3
    KEY3 = xor(KEY2, KEY2_xor_KEY3)
    
    # Step 4: XOR FLAG expression with all keys
    FLAG = xor(FLAG_xor_all, xor(KEY1, xor(KEY2, KEY3)))
    
    print("FLAG:", FLAG.decode())
output:crypto{x0r_i5_ass0c1at1v3}


3)FAVOURITE BITE


      import binascii
      
      # Step 1: Hex decode
      hex_str = "73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d"
      data = bytes.fromhex(hex_str)
      
      # Step 2: Brute-force single-byte key
      for key in range(256):
          decoded = bytes([b ^ key for b in data])
          try:
              text = decoded.decode()
              if "crypto" in text:
                  print(f"Key: {key} -> {text}")
                  break
          except:
              continue


  output:crypto{0x10_15_my_f4v0ur173_by7e}

  4)EITHER YOU KNOW XOR OR NOT


        # === Given Data ===
      cipher_hex = "0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104"
      cipher_bytes = bytes.fromhex(cipher_hex)
      
      # Known starting text of plaintext (CryptoHack flags start like this)
      known_text = b"crypto{"
      
      # === Step 1: Recover part of the key ===
      key = bytes([c ^ p for c, p in zip(cipher_bytes, known_text)])
      print("Recovered key so far:", key)
      
      # If key is shorter than full message, assume it's repeating
      # Let's try decrypting using the repeating key
      def xor_repeating(data, key):
          return bytes([b ^ key[i % len(key)] for i, b in enumerate(data)])
      
      # === Step 2: Decrypt the message ===
      decrypted = xor_repeating(cipher_bytes, key)
      print("Decrypted message:", decrypted.decode())

output:Decrypted message: crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}  (i tried with key= b'myXORke' but it wasn't complete and gave me some gibberish

