# dependency injection

## static class

```c#
using level_2_reference.controllers.DTOs;
using level_2_reference.Entities;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Runtime.CompilerServices;
using System.Text;
using System.Threading.Tasks;

namespace level_2_reference.services.mappers
{
    /// <summary>
    /// classes with extension methods - are always public and static
    /// </summary>
    public static class SomeMapper
    {
        /// <summary>
        /// extension methods - are always public and static, use 'this' for parameter
        /// </summary>
        /// <param name="entity">works as extension method by using 'this' as parameter</param>
        /// <returns></returns>
        public static SomeDTO MapToDTO(this SomeEntity entity)
        {
            // map entity to dto

            return new SomeDTO { SomeProperty1 = entity.SomeProperty1.ToString(),
            SomeProperty2 = entity.SomeProperty2.ToString(),
            SomeProperty3 = entity.SomeProperty3.ToShortDateString()
            };
        }

        /// <summary>
        /// extension methods - are always public and static, use 'this' for parameter
        /// </summary>
        /// <param name="dto">works as extension method by using 'this' as parameter</param>
        /// <returns></returns>
        public static SomeEntity MapToEntity(this SomeDTO dto) {

            // map dto to entity

            bool boolToParse = bool.Parse(dto.SomeProperty1);
            double doubleToParse = double.Parse(dto.SomeProperty2);
            DateTime dateToParse = DateTime.Parse(dto.SomeProperty3);

            return new SomeEntity
            {
                SomeProperty1 = boolToParse,
                SomeProperty2 = doubleToParse,
                SomeProperty3 = dateToParse
            };
        }
    }
}
```

## implementation

```c#
using level_2_reference.controllers.DTOs;
using level_2_reference.Entities;
using level_2_reference.helpers;
using level_2_reference.helpers.abstraction;
using level_2_reference.repos.abstraction;
using level_2_reference.services.abstraction;
using level_2_reference.services.exceptions;
using level_2_reference.services.mappers;
using System;
using System.Collections.Generic;
using System.Dynamic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace level_2_reference.services.implement
{
    /// <summary>
    /// services - contain business logic, validation, aggragetion of data from repos, call repos, domain specific logic
    /// </summary>
    public class SomeService:ISomeService
    {
        private ILogger _logger;
        private ISomeRepository _repo;

        // constructors inject interface
        public SomeService(ILogger logger, ISomeRepository repo)
        {
            _logger = logger;
            _repo = repo;
        }

        public async Task CreateSomeDTO(SomeDTO dto)
        {
            await _logger.LogAsync("log message");

            // map dto to entity using extension method

            SomeEntity entityToCreate = dto.MapToEntity();

            // some validation using helper static method

            if (SomeHelper.CalcSomething(entityToCreate.SomeProperty2, entityToCreate.SomeProperty1) != 100) {

            throw new SomeFunctionalException("invalid entry");
            }

            // call repo
            await _repo.CreateSomeEntityAsync(entityToCreate);
        }

        public async Task<SomeDTO> GetSomeDTO()
        {
            // call repo

            List<SomeEntity> listToSort = await _repo.GetSomeEntityListAsync();

            SomeDTO someDTOtoReturn = new SomeDTO();

            // imperative vs. declarative coding

            // declarative using linq in list

            SomeEntity entityToFind = (from entity
                          in listToSort
                          where entity.SomeProperty2 > 8
                          select entity).ToList().First();


            // validation/domain logic
            if (entityToFind.SomeProperty2.ToString().Length > 15) {
                throw new SomeFunctionalException("property value to long");
            }

            // declarative using link method chain

            SomeEntity entityToFind2 = listToSort.Where(c => c.SomeProperty3 == DateTime.Today).Select(i=> i).First();
            // someDTOtoReturn.SomeProperty2 = entityToFind.SomeProperty2.ToString();

            // validation/domain logic
            if (entityToFind.SomeProperty3.ToShortDateString().Contains("February"))
            {
                throw new SomeFunctionalException("service not available on Fbruary");
            }

            SomeEntity someEntityToFind3 = new SomeEntity();
            // someDTOtoReturn.SomeProperty3 = entityToFind2.SomeProperty3.ToShortDateString();


            // imperative using foreach + if

            foreach (var entity in listToSort)
            {
                if (entity.SomeProperty1 == false)
                {
                    someEntityToFind3 = entity;
                }
            }

            // someDTOtoReturn.SomeProperty1 = someEntityToFind3.SomeProperty1.ToString();

            // call mapper extension method
            someDTOtoReturn = someEntityToFind3.MapToDTO();

            await _logger.LogAsync(someDTOtoReturn.SomeProperty1);

            return someDTOtoReturn;
        }


    }
}
```
