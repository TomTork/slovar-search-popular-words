# slovar-search-popular-words
import pymorphy2

f = [i

     .replace('!', '')
     .replace('?', '')
     .replace('(', '')
     .replace(')', '').replace('\n', '')
     .replace(':', '').replace(';', '')
     .replace('—', '').split(' ')
     for i in open('text.txt', 'r', encoding='utf-8').readlines()]

d = {}
m = pymorphy2.MorphAnalyzer()
for i in f:
    for t in i:
        morph = m.parse(t)[0].normal_form
        if morph not in d:
            d[morph] = 1
        else:
            d[morph] += 1

print(d)

print(sorted(list(set(d.values())), reverse=True))

k = 0
print(len(d))
