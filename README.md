Реализация функции curry:

        let curry = function (fn) {
                let fnLength = fn.length;
                console.log('fnLength', fnLength);

                return function f1(...args) {
                  console.log('f1 args', args);
                  if (args.length >= fnLength) {
                    console.log('enough arguments');
                    return fn(...args);
                  } else {
                    console.log('need more arguments')
                    return function f2(...moreArgs) {
                      console.log('f2', moreArgs);
                      let newArgs = args.concat(moreArgs);
                      return f1(...newArgs);
                    };
                  }
                };
              };

              let abc = function (a, b, c) {
                return a + b + c;
              };

              let abcdef = function (a, b, c, d, e, f) {
                return a + b + c + d + e + f;
              };

              let curriedAbc = curry(abc);
              let curriedAbcdef = curry(abcdef);

              let resultAbc = curriedAbc("A", "B", "C");
              let resultAbcdef = curriedAbcdef('A', 'B', 'C')('D', 'E', 'F');


              console.log('resultAbc', resultAbc);
              console.log('resultAbcdef', resultAbcdef);
