import random
import time

class FoodExplorer:
    def __init__(self):
        # 內建的美食資料庫
        self.food_database = {
            "日式料理": ["濃厚豚骨拉麵", "迴轉壽司", "日式炸豬排", "居酒屋串燒"],
            "台式在地": ["經典滷肉飯", "紅燒牛肉麵", "巷口乾麵", "夜市牛排"],
            "異國風味": ["義式窯烤披薩", "美式經典漢堡", "泰式打拋豬", "印度咖哩"],
            "甜點輕食": ["手搖珍珠奶茶", "法式千層蛋糕", "文青咖啡廳", "焦糖布丁"]
        }
        
    def welcome(self):
        print("="*32)
        print("  🍽️ 歡迎來到【美食探索家】 🍽️  ")
        print("="*32)
        print("不知道今天該吃什麼嗎？讓我來幫你探索！\n")

    def random_recommend(self):
        category = random.choice(list(self.food_database.keys()))
        food = random.choice(self.food_database[category])
        print("🔍 正在為您探索美食...")
        time.sleep(1) # 製造探索的期待感
        print(f"✨ 探索結果：推薦您嘗試【{category}】的「{food}」！\n")

    def browse_category(self):
        print("\n請選擇想探索的類別：")
        categories = list(self.food_database.keys())
        for i, cat in enumerate(categories, 1):
            print(f"{i}. {cat}")
        
        try:
            choice = int(input("輸入數字選擇 (1-4): "))
            if 1 <= choice <= len(categories):
                selected_cat = categories[choice-1]
                foods = "、".join(self.food_database[selected_cat])
                print(f"\n📂 【{selected_cat}】的美食庫有：\n{foods}\n")
            else:
                print("⚠️ 輸入錯誤，請輸入列表中的數字。\n")
        except ValueError:
            print("⚠️ 格式錯誤，請輸入數字！\n")

    def run(self):
        self.welcome()
        while True:
            print("1. 🎲 隨機推薦美食")
            print("2. 🗂️ 瀏覽美食分類")
            print("3. 🚪 退出程式")
            choice = input("👉 請選擇功能 (1/2/3): ")
            
            if choice == '1':
                self.random_recommend()
            elif choice == '2':
                self.browse_category()
            elif choice == '3':
                print("\n感謝使用【美食探索家】，祝您用餐愉快！再見 👋")
                break
            else:
                print("⚠️ 無效的選擇，請重新輸入。\n")

if __name__ == "__main__":
    app = FoodExplorer()
    app.run()
