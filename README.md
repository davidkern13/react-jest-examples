# react-jest-examples


```Javascript

import React from 'react';

describe("use state test", () => {

    const setState = jest.fn();
    const useStateSpy = jest.spyOn(React, 'useState'); //appropriate for overwrite the original function
    useStateSpy.mockImplementation((init) => [init, setState]); //Accepts a function that should be used as the implementation of the mock.
    
    afterEach(() => {
      jest.clearAllMocks();
    });
    
    test("mock useState and update with value", () =>{
        //trigger setState
        setState();
        expect(setState).toHaveBeenCalledTimes(1);

        setState(1);
        expect(setState).toHaveBeenCalledWith(1);
    });
});

```
